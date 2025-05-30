```
ICA
```

独立成分分析モデルを構築するためのモデルタイプで、[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づき、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
ICA = @load ICA pkg=MultivariateStats
```

`model = ICA()`を実行して、デフォルトのハイパーパラメータでインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`ICA(outdim=...)`のようにキーワード引数を提供します。

独立成分分析は、多変量信号を加法的なサブコンポーネントに分離するための計算技術であり、サブコンポーネントが非ガウス的で互いに独立しているという仮定に基づいています。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてデータにインスタンス`model`をバインドします。

```
mach = machine(model, X)
```

ここで：

  * `X`は、列がスカイタイプ`Continuous`の任意の入力特徴のテーブル（例：`DataFrame`）です。列のスカイタイプは`schema(X)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `outdim::Int=0`: 回復する独立成分の数。`0`の場合は自動的に設定されます。
  * `alg::Symbol=:fastica`: 使用するアルゴリズム（現時点では`：fastica`のみがサポートされています）。
  * `fun::Symbol=:tanh`: 近似ネガエントロピー関数。`:tanh`、`:gaus`のいずれか。
  * `do_whiten::Bool=true`: 前処理のホワイトニングを行うかどうか。
  * `maxiter::Int=100`: 最大反復回数。
  * `tol::Real=1e-6`: 混合行列Wの変化に対する収束許容値。
  * `mean::Union{Nothing, Real, Vector{Float64}}=nothing`: 使用する平均。何も指定しない場合（デフォルト）には中心化が計算され適用され、ゼロの場合は中心化されません。それ以外の場合は平均のベクトルを渡すことができます。
  * `winit::Union{Nothing,Matrix{<:Real}}=nothing`: 混合行列`W`の初期推定値：空の行列（`W`のランダム初期化用）、サイズ`m × k`の行列（`do_whiten`がtrueの場合）、またはサイズ`m × k`の行列のいずれかです。ここで`m`は入力の成分（列）の数です。

# 操作

  * `transform(mach, Xnew)`: 入力`Xnew`の成分分離バージョンを返します。`X`と同じスカイタイプである必要があります。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `projection`: 推定された成分行列。
  * `mean`: 推定された平均ベクトル。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `indim`: トレーニングデータと変換される新しいデータの次元（列数）。
  * `outdim`: 変換されたデータの次元。
  * `mean`: 変換されていないトレーニングデータの平均で、長さは`indim`です。

# 例

```
using MLJ

ICA = @load ICA pkg=MultivariateStats

times = range(0, 8, length=2000)

sine_wave = sin.(2*times)
square_wave = sign.(sin.(3*times))
sawtooth_wave = map(t -> mod(2t, 2) - 1, times)
signals = hcat(sine_wave, square_wave, sawtooth_wave)
noisy_signals = signals + 0.2*randn(size(signals))

mixing_matrix = [ 1 1 1; 0.5 2 1; 1.5 1 2]
X = MLJ.table(noisy_signals*mixing_matrix)

model = ICA(outdim = 3, tol=0.1)
mach = machine(model, X) |> fit!

X_unmixed = transform(mach, X)

using Plots

plot(X.x2)
plot(X.x2)
plot(X.x3)

plot(X_unmixed.x1)
plot(X_unmixed.x2)
plot(X_unmixed.x3)

```

他の情報については、[`PCA`](@ref)、[`KernelPCA`](@ref)、[`FactorAnalysis`](@ref)、[`PPCA`](@ref)を参照してください。
