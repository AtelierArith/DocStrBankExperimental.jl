```
KernelPCA
```

カーネル主成分分析モデルを構築するためのモデルタイプで、[MultivariateStats.jl](https://github.com/JuliaStats/MultivariateStats.jl)に基づいており、MLJモデルインターフェースを実装しています。

MLJからは、次のようにしてタイプをインポートできます。

```
KernelPCA = @load KernelPCA pkg=MultivariateStats
```

`model = KernelPCA()`を実行して、デフォルトのハイパーパラメータを持つインスタンスを構築します。ハイパーパラメータのデフォルトを上書きするには、`KernelPCA(maxoutdim=...)`のようにキーワード引数を提供します。

カーネルPCAでは、通常の主成分分析の線形操作が[再生ヒルベルト空間](https://en.wikipedia.org/wiki/Reproducing_kernel_Hilbert_space)で行われます。

# トレーニングデータ

MLJまたはMLJBaseでは、次のようにしてインスタンス`model`をデータにバインドします。

```
mach = machine(model, X)
```

ここで：

  * `X`は、列がscitype `Continuous`の任意の入力特徴のテーブル（例：`DataFrame`）です。列のscitypeは`schema(X)`で確認できます。

`fit!(mach, rows=...)`を使用してマシンをトレーニングします。

# ハイパーパラメータ

  * `maxoutdim=0`: 出力の次元（列数）`outdim`を制御します。具体的には、`outdim = min(n, indim, maxoutdim)`で、ここで`n`は観測数、`indim`は入力次元です。
  * `kernel::Function=(x,y)->x'y`: カーネル関数で、2つのベクトル引数xとyを受け取り、スカラー値を返します。デフォルトは`x`と`y`のドット積です。
  * `solver::Symbol=:eig`: 固有値に使用するソルバーで、`:eig`（デフォルト、`LinearAlgebra.eigen`を使用）、`:eigs`（`Arpack.eigs`を使用）のいずれかです。
  * `inverse::Bool=true`: 逆変換に必要な計算を実行します。
  * `beta::Real=1.0`: 逆が真のときに逆変換を学習するリッジ回帰の強さです。
  * `tol::Real=0.0`: 固有値ソルバーの収束許容値です。
  * `maxiter::Int=300`: 固有値ソルバーの最大反復回数です。

# 操作

  * `transform(mach, Xnew)`: 入力`Xnew`の低次元投影を返します。`X`と同じscitypeを持つ必要があります。
  * `inverse_transform(mach, Xsmall)`: `transform`によって返された次元削減されたテーブル`Xsmall`に対して、元のトレーニングデータ`X`と同じ列数を持つテーブルを再構築し、`Xsmall`に変換します。数学的には、`inverse_transform`はPCA投影マップの右逆であり、その像はそのマップのカーネルに直交します。特に、`Xsmall = transform(mach, Xnew)`の場合、`inverse_transform(Xsmall)`は`Xnew`への近似に過ぎません。

# フィッティングパラメータ

`fitted_params(mach)`のフィールドは次のとおりです。

  * `projection`: 投影行列を返します。サイズは`(indim, outdim)`で、`indim`と`outdim`はそれぞれ入力と出力の特徴の数です。

# レポート

`report(mach)`のフィールドは次のとおりです。

  * `indim`: トレーニングデータと変換される新しいデータの次元（列数）。
  * `outdim`: 変換されたデータの次元。
  * `principalvars`: 主成分の分散。

# 例

```
using MLJ
using LinearAlgebra

KernelPCA = @load KernelPCA pkg=MultivariateStats

X, y = @load_iris # テーブルとベクトル

function rbf_kernel(length_scale)
    return (x,y) -> norm(x-y)^2 / ((2 * length_scale)^2)
end

model = KernelPCA(maxoutdim=2, kernel=rbf_kernel(1))
mach = machine(model, X) |> fit!

Xproj = transform(mach, X)
```

他にも[`PCA`](@ref)、[`ICA`](@ref)、[`FactorAnalysis`](@ref)、[`PPCA`](@ref)を参照してください。
