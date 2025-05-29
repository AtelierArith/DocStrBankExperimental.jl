# Juliaにおけるロバスト線形モデル

|                                   ドキュメンテーション                                    |       CI ステータス        |              カバレッジ              |
|:-------------------------------------------------------------------------------:|:---------------------:|:-------------------------------:|
| [![][docs-stable-img]][docs-stable-url] [![][docs-latest-img]][docs-latest-url] | [![][CI-img]][CI-url] | [![][codecov-img]][codecov-url] |

[docs-latest-img]: https://img.shields.io/badge/docs-latest-blue.svg [docs-latest-url]: https://getzze.github.io/RobustModels.jl/dev

[docs-stable-img]: https://img.shields.io/badge/docs-stable-blue.svg [docs-stable-url]: https://getzze.github.io/RobustModels.jl/stable

[CI-img]: https://github.com/getzze/RobustModels.jl/workflows/CI/badge.svg [CI-url]: https://github.com/getzze/RobustModels.jl/actions

[codecov-img]: https://img.shields.io/codecov/c/github/getzze/RobustModels.jl?label=Codecov&logo=codecov [codecov-url]: https://codecov.io/gh/getzze/RobustModels.jl/branch/master

このパッケージは、[StatsBase.jl](https://github.com/JuliaStats/StatsBase.jl)および[StatsModels.jl](https://github.com/JuliaStats/StatsModels.jl)のインターフェースを使用してロバスト線形モデルを定義します。`RegressionModel`のサブタイプとして`AbstractRobustModel`型を定義し、`fit`/`fit!`のような統計モデルAPIのメソッドを定義します。

*ロバストモデル*は回帰モデルであり、1つまたは複数の*共変量/独立変数*`X`と*応答/従属*変数`y`との関係を見つけます。通常の最小二乗推定とは異なり、ロバスト回帰はデータ内の*外れ値*の影響を軽減します。`RobustLinearModel`の標準的な見方は、残差が*汚染された*分布に従うと考えることです。つまり、関心のある分布`F`とより高い分散を持つ汚染分布`Δ`の*混合モデル*です。したがって、残差`r`は分布`r ~ (1-ε) F + ε Δ`に従い、`0≤ε<1`です。

このパッケージは以下を実装しています：

  * M推定量
  * S推定量
  * MM推定量
  * τ推定量
  * M分位回帰（例：期待値回帰）
  * ロバストリッジ回帰（前述の推定量のいずれかを使用）
  * 内点法を使用した分位回帰

## インストール

```
julia>] add RobustModels
```

最新の開発バージョンをインストールするには：

```
julia>] add RobustModels#main
```

## 使用法

ロバスト回帰を実行するための推奨方法は、`rlm`関数を呼び出すことです：

`m = rlm(X, y, MEstimator{TukeyLoss}(); initial_scale=:mad)`

分位回帰には`quantreg`を使用します：

`m = quantreg(X, y; quantile=0.5)`

ロバスト版の`mean`、`std`、`var`および`sem`統計を使用するには、最初の引数として推定量を指定します。特定の次元に沿って統計を計算するには、`dims`キーワードを使用します。以下の関数も実装されています：`mean_and_std`、`mean_and_var`および`mean_and_sem`。

`xm = mean(MEstimator{HuberLoss}(), x; dims=2)`

`(xm, sm) = mean_and_std(TauEstimator{YohaiZamarLoss}(), x)`

## 例

```jldoctest; output = false
using RDatasets: dataset
using StatsModels
using RobustModels

data = dataset("robustbase", "Animals2")
data.logBrain = log.(data.Brain)
data.logBody = log.(data.Body)
form = @formula(logBrain ~ 1 + logBody)

## Tukey推定量を使用したM推定量
m1 = rlm(form, data, MEstimator{TukeyLoss}(); method=:cg, initial_scale=:mad)

## Tukey推定量を使用したMM推定量
m2 = rlm(form, data, MMEstimator{TukeyLoss}(); method=:cg, initial_scale=:L1)

## Huber推定量を使用したM推定量および共変量外れ値の補正
m3 = rlm(form, data, MEstimator{HuberLoss}(); method=:cg, initial_scale=:L1, correct_leverage=true)

## Huber推定量を使用したM推定量、初期スケール推定を提供し、Cholesky法を使用して解決。
m4 = rlm(form, data, MEstimator{HuberLoss}(); method=:chol, initial_scale=15.0)

## Tukey推定量を使用したS推定量
m5 = rlm(form, data, SEstimator{TukeyLoss}(); σ0=:mad)

## Tukey推定量を使用したτ推定量
m6 = rlm(form, data, TauEstimator{TukeyLoss}(); initial_scale=:L1)

## YohaiZamar推定量を使用したτ推定量およびリサンプリングによるグローバル最小値の探索
opts = Dict(:Npoints=>10, :Nsteps_β=>3, :Nsteps_σ=>3)
m7 = rlm(form, data, TauEstimator{YohaiZamarLoss}(); initial_scale=:L1, resample=true, resampling_options=opts)

## τ=0.8の期待値回帰
m8 = rlm(form, data, GeneralizedQuantileEstimator{L2Loss}(0.8))
#m8 = rlm(form, data, ExpectileEstimator(0.8))

## 異なるパラメータで再フィット
refit!(m8; quantile=0.2)

## ロバストリッジ回帰
m9 = rlm(form, data, MEstimator{TukeyLoss}(); initial_scale=:L1, ridgeλ=1.0)

## 線形プログラミング内点法によって解決された分位回帰
m10 = quantreg(form, data; quantile=0.2)
refit!(m10; quantile=0.8)
;

# 出力

```

## 理論

### M推定量

通常の最小二乗法（OLS）では、目的関数は最大尤度推定から次のようになります：

`L = ½ Σᵢ (yᵢ - 𝒙ᵢ 𝜷)² = ½ Σᵢ rᵢ²`

ここで、`yᵢ`は応答変数の値、`𝒙ᵢ`は個々の共変量の共ベクトル（モデル行列`X`の行）、`𝜷`はフィットした係数のベクトル、`rᵢ`は個々の残差です。

`RobustLinearModel`は、次の損失関数を解決します：`L' = Σᵢ ρ(rᵢ)`（より正確には`L' = Σᵢ ρ(rᵢ/σ)`、ここで`σ`は残差の標準偏差の（ロバストな）推定値です）。いくつかの損失関数が実装されています：

  * `L2Loss`: `ρ(r) = ½ r²`、通常のOLSのように。
  * `L1Loss`: `ρ(r) = |r|`、微分不可能な推定量で、*最小絶対偏差*としても知られています。`QuantileRegression`ソルバーを優先してください。
  * `HuberLoss`: `ρ(r) = if (r<c); ½(r/c)² else |r|/c - ½ end`、小さな残差に対しては`L2`コストとして振る舞い、大きな残差や外れ値に対しては`L1`として振る舞う凸推定量です。
  * `L1L2Loss`: `ρ(r) = √(1 + (r/c)²) - 1`、`HuberLoss`の滑らかなバージョンです。
  * `FairLoss`: `ρ(r) = |r|/c - log(1 + |r|/c)`、`HuberLoss`の滑らかなバージョンです。
  * `LogcoshLoss`: `ρ(r) = log(cosh(r/c))`、`HuberLoss`の滑らかなバージョンです。
  * `ArctanLoss`: `ρ(r) = r/c * atan(r/c) - ½ log(1+(r/c)²)`、`HuberLoss`の滑らかなバージョンです。
  * `CauchyLoss`: `ρ(r) = log(1+(r/c)²)`、非凸推定量で、固定された自由度のStudentのt分布にも対応します。外れ値をより強く抑制しますが、収束するかどうかは不明です。
  * `GemanLoss`: `ρ(r) = ½ (r/c)²/(1 + (r/c)²)`、非凸で有界な推定量で、外れ値をより強く抑制します。
  * `WelschLoss`: `ρ(r) = ½ (1 - exp(-(r/c)²))`、非凸で有界な推定量で、外れ値をより強く抑制します。
  * `TukeyLoss`: `ρ(r) = if r<c; ⅙(1 - (1-(r/c)²)³) else ⅙ end`、非凸で有界な推定量で、外れ値をより強く抑制し、ほとんどのケースで推奨される推定量です。
  * `YohaiZamarLoss`: `ρ(r)`は`r/c < 2/3`のとき二次で、1に制限されます；非凸推定量で、与えられた効率に対して最も低いバイアスを持つように最適化されています。

調整定数`c`の値は各推定量に対して最適化されているため、M推定量は高い効率を持ち、0.95です。ただし、これらの推定量は低いブレークダウンポイントを持ちます。

### S推定量

`Σᵢ ρ(rᵢ/σ)`を最小化する代わりに、S推定は次の制約の下で平方スケール`σ²`の推定値を最小化します：`1/n Σᵢ ρ(rᵢ/σ) = 1/2`。S推定量は、`TukeyLoss`のような有界推定量に対してのみ定義されています。これらの推定量は効率が低いですが、調整定数`c`を適切に選ぶことで1/2の高いブレークダウンポイントを持ちます。

### MM推定量

これは二段階の推定で、1) 高いブレークダウンポイントを持つS推定を使用して`σ`を推定し、2) 高い効率を持つM推定を使用して`𝜷`を推定します。これにより、高い効率と高いブレークダウンポイントを持つ推定量が得られます。

### τ推定量

MM推定量と同様に、τ推定量は高い効率と高いブレークダウンポイントを組み合わせます。S推定量と同様に、スケール推定を最小化します：`τ² = σ² (2/n Σᵢρ₂(rᵢ/σ))`、ここで`σ`はMスケール推定で、`1/n Σᵢ ρ₁(rᵢ/σ) = 1/2`の解です。τ推定量の最小値を見つけることは、両方の関数`ρ₁`と`ρ₂`を組み合わせた特別な重み関数を持つS推定量の手順に似ています。高いブレークダウンポイントと高い効率を確保するために、2つの損失関数は同じであるべきですが、異なる調整定数を持つべきです。

### MQuantile推定量

非対称の`L1Estimator`のバリアントを使用して分位回帰が行われます（ただし、正確な解を提供するため、`QuantileRegression`ソルバーを優先すべきです）。同様に、損失関数の非対称バージョンを使用したM推定を使用することで、分位数の一般化が得られます。たとえば、非対称の`L2Loss`を使用すると*期待値回帰*が得られます。

### ロバストリッジ回帰

これはリッジ回帰のロバスト版で、係数にペナルティを追加します。解決すべき目的関数は`L = Σᵢ ρ(rᵢ/σ) + λ Σⱼ|βⱼ|²`であり、係数の二乗和には切片`β₀`は含まれません。ロバストリッジ回帰はすべての推定量に対して実装されています（`quantreg`には実装されていません）。デフォルトでは、すべての係数（切片を除く）は同じペナルティを持ち、すべての特徴変数が同じスケールを持つと仮定します。そうでない場合は、回帰をフィットさせる前にモデル行列`X`の各列を正規化するためにロバストなスケールの推定を使用してください。

### 分位回帰

*分位回帰*は、次の目的関数を最小化することから生じます：`L = Σᵢ wᵢ|yᵢ - 𝒙ᵢ 𝜷| = Σᵢ wᵢ(rᵢ) |rᵢ|`、ここで`wᵢ = ifelse(rᵢ>0, τ, 1-τ)`であり、`τ`は関心のある分位数です。`τ=0.5`は*最小絶対偏差*に対応します。

この問題は、線形プログラミング技術、特に[内点法](https://github.com/ds4dm/Tulip.jl)を使用して正確に解決されます。内部APIは不安定と見なされますが、[JuMP](https://github.com/JuliaOpt/JuMP.jl)パッケージをTulipバックエンドと共に含めるよりもはるかに軽い依存関係をもたらします。

## クレジット

このパッケージは、初期実装のための[RobustLeastSquares](https://github.com/FugroRoames/RobustLeastSquares.jl)パッケージに由来し、特に共役勾配ソルバーとM推定関数の定義に関してです。

[GLM](https://github.com/JuliaStats/GLM.jl)および[MixedModels](https://github.com/JuliaStats/MixedModels.jl)パッケージの開発者に感謝します。彼らは反復加重最小二乗法アルゴリズムを実装しました。

## 参考文献

  * "Robust Statistics: Theory and Methods (with R)", 2nd Edition, 2019, R. Maronna, R. Martin, V. Yohai, M. Salibián-Barrera
