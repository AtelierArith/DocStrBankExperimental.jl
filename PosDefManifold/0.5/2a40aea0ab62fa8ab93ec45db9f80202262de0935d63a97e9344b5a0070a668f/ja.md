```julia
    (1) spectralEmbedding(metric::Metric, 𝐐::ℍVector, q::Int, epsilon::Real=0;
    <
    tol::Real=0.,
    maxiter::Int=300,
    densityInvariant=false,
    verbose=false,
    ⏩=true >)

    (2) spectralEmbedding(type::Type{T}, metric::Metric, 𝐐::ℍVector, q::Int, epsilon::Real=0;
    < (1)と同じオプションのキーワード引数 >) where T<:Real
```

**エイリアス**: `spEmb`

$$
k
$$

個の正定値行列${P_1,...,P_k}$（実数または複素数）の1次元配列$𝐐$を与えられたとき、$q$次元での*固有マップ*を計算します。

この関数は、次の関数を順次実行します：

  * [`distanceSqrMat`](@ref)（二乗間距離行列を計算）、
  * [`laplacian`](@ref)（正規化ラプラシアンを計算）、
  * [`laplacianEigenMaps`](@ref)（固有マップを取得）。

デフォルトでは、上記のすべての計算は`Float32`精度で行われます。別の実数型は、`type`引数が定義されるメソッド(2)を使用して要求できます。

4タプル`(Λ, U, iterations, convergence)`を返します。ここで：

  * $$
    Λ
    $$

    は、ラプラシアン固有マップの$q$次元に対応する固有値を対角に保持する$q⋅q$対角行列です。
  * $$
    U
    $$

    は、埋め込み空間内の点の$q$座標を保持する$q$固有ベクトルを列に保持します。
  * $$
    iterations
    $$

    は、冪法によって実行された反復の数です。
  * $$
    convergence
    $$

    は、冪法によって達成された収束です。

**引数**：

  * `metric`は、間距離を計算するために使用される[Metric::列挙型](@ref)のメトリックです。
  * $$
    𝐐
    $$

    は、[ℍVector型](@ref)の$k$個の正の行列の1次元配列です。
  * $$
    q
    $$

    は、ラプラシアン固有マップの次元です。
  * $$
    epsilon
    $$

    は、ラプラシアンの帯域幅です（[`laplacian`](@ref)を参照）。
  * 次の*<オプションのキーワード引数>*は、間距離を計算するために適用されます：
  * `⏩=true`（デフォルト）の場合、間距離の計算はマルチスレッドで行われます。
  * 次の*<オプションのキーワード引数>*は、[`laplacian`](@ref)関数によるラプラシアンの計算に適用されます：
  * `densityInvariant=true`の場合、密度不変ラプラシアンが計算されます（[`laplacian`](@ref)を参照）。
  * 次の*<オプションのキーワード引数>*は、[`laplacianEigenMaps`](@ref)によって呼び出される冪法反復アルゴリズムのためのものです：

      * `tol`は、冪法の収束のための許容誤差です（以下を参照）。
      * `maxiter`は、冪法に許可される最大反復回数です。
      * `verbose=true`の場合、すべての反復での収束が表示されます。

!!! note "Nota Bene"
    $$
    tol
    $$

    は、`Float32`型（1）または引数（2）として渡された`type`の`Base.eps`の平方根にデフォルト設定されています。これは、約半分の有効数字に対する2回の連続した冪反復の収束基準の等価性を要求することに相当します。

    [マルチスレッド](https://docs.julialang.org/en/v1/manual/parallel-computing/#Multi-Threading-(Experimental)-1)は、Juliaが1つのスレッドのみを使用するように指示されている場合、自動的に無効になります。[Threads](@ref)を参照してください。


**関連項目**: [`distanceSqrMat`](@ref), [`laplacian`](@ref), [`laplacianEigenMaps`](@ref)。

**例**

```julia
using PosDefManifold
# k個のランダムな10x10 SPD行列のセットを生成
k=10
Pset=randP(10, k)
evalues, maps, iter, conv=spectralEmbedding(Fisher, Pset, 2)

# 収束情報を表示
evalues, maps, iter, conv=spectralEmbedding(Fisher, Pset, 2; verbose=true)

# Float64精度を使用。
evalues, maps, iter, conv=spectralEmbedding(Float64, Fisher, Pset, 2)

using Plots
# 固有値と固有ベクトルを確認
plot(diag(evalues))
plot(maps[:, 1])
plot!(maps[:, 2])
plot!(maps[:, 3])

# 埋め込まれた空間内のデータをプロット
plot(maps[:, 1], maps[:, 2], seriestype=:scatter, title="スペクトル埋め込み", label="Pset")

# epsilonの異なる値を試す
evalues, maps, iter, conv=spEmb(Fisher, Pset, k-1, 0.01; maxiter=1000)
plot(maps[:, 1], maps[:, 2], seriestype=:scatter, title="スペクトル埋め込み", label="Pset")
# これに関する詳細は`Laplacian`関数の例を参照してください
```
