```
GPR
```

GPRは、[MLJGaussianProcesses.jl](https://github.com/john-waczak/MLJGaussianProcesses.jl)に基づいてgprを構築するためのモデルタイプであり、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
GPR = @load GPR pkg=MLJGaussianProcesses
```

デフォルトのハイパーパラメータでインスタンスを構築するには、`model = GPR()`を実行します。ハイパーパラメータのデフォルトをオーバーライドするには、`GPR(μ=...)`のようにキーワード引数を提供します。MLJGaussianProcessesは、[Gaussian Process Regression](https://gaussianprocess.org/gpml/chapters/RW2.pdf)を実装しており、これは、[JuliaGaussianProcesses](https://juliagaussianprocesses.github.io/)組織のツールを利用した、教師あり機械学習のための非パラメトリックで非線形の回帰モデルです。

# トレーニングデータ

MLJまたはMLJBaseでは、`mach = machine(model, X, y)`を使用してデータにインスタンス`model`をバインドします。ここで、

  * `X`: 列がscitype `Continuous`の入力特徴の`AbstractMatrix`または`Table`です。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

  * `y`: scitype `Continuous`のターゲット変数の`Vector`です。

# ハイパーパラメータ

  * `μ=0`: ガウス過程の平均関数に使用する定数値。
  * `k=default_kernel`: パラメータ`θ`を受け取り、`KernelFunction`を返す関数`k(θ)`。`default_kernel`は、分散`σf²`と長さスケール`ℓ`を持つ古典的なRBFカーネルです。
  * `θ_init=θ_default`: 最適化を初期化するためのデフォルトパラメータ。デフォルトカーネルのために`θ_default = (1.0, 1.0)`にデフォルト設定されています。
  * `σ²=1e-6`: 測定ノイズ（分散）。内部のコレスキー因子分解の安定性を確保するために`0`より大きくする必要があります。
  * `optimizer:LBFGS()`: `Optim.jl`からのオプティマイザ。

# 操作

  * `predict(mach, X)`: 各予測ターゲットの正規分布のベクトルを返します。
  * `predict_mean(mach, X)`: 予測ターゲットの分布からの平均のベクトルを返します。
  * `predict_mode(mach, X)`: 予測ターゲットの分布からのモードのベクトルを返します。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `θ_best`: GPRフィット中に見つかった最良のパラメータの名前付きタプル。
  * `σ²`: 測定分散の最良フィット。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `summary`: 最適化の結果の要約。
  * `minimizer`: GPRモデルの周辺対数尤度を最小化したパラメータ。
  * `minimum`: 最適化中の周辺対数尤度の最小値。
  * `iterations`: オプティマイザが取ったステップの数。
  * `converged`: 最適化スキームが割り当てられた反復回数で収束したかどうか。

# 例

```
using MLJ
gpr = @load GPR pkg=MLJGaussianProcesses
model = gpr()
X, y = make_regression(50, 3) # 合成データ
mach = machine(model, X, y) |> fit!
p_y = predict(mach, X)
ŷ = predict_mean(mach, X)
rpt = report(mach)
```
