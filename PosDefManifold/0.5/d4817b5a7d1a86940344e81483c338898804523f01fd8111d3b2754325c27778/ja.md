```julia
    laplacianEigenMaps(Ω::𝕃{S}, q::Int;
    <
    tol::Real=0.,
    maxiter::Int=300,
    verbose=false >) where S<:Real
```

**エイリアス**: `laplacianEM`

下三角部分のラプラシアン $Ω$ (see [`laplacian`](@ref) ) を与えられたとき、*固有マップ*を $q$ 次元で返します。すなわち、最初の固有値（常に 1.0 に等しい）を除く、ラプラシアンに関連する最大の $q$ 固有値の $q$ 固有ベクトルです。固有ベクトルは $Ω$ と同じ型です。すべての固有ベクトルは最初の固有ベクトルで要素ごとに割られます（see Lafon, 2004[🎓](@ref)）。

ラプラシアンの固有ベクトルは、パワー反復 + 修正グラム・シュミット法（see [`powerIterations`](@ref)）によって計算され、非常に大きなサイズのラプラシアン行列に対してこの関数を実行できるようにします。

4-タプル $(Λ, U, iterations, convergence)$ を返します。ここで：

  * $$
    Λ
    $$

    は $q⋅q$ 対角行列で、ラプラシアン固有マップの $q$ 次元に対応する固有値を対角に保持します。
  * $$
    U
    $$

    は列に $q$ 固有ベクトルを保持し、埋め込み空間の点の $q$ 座標を保持します。
  * $$
    iterations
    $$

    はパワー法によって実行された反復の回数です。
  * $$
    convergence
    $$

    はパワー法によって達成された収束です。

ラプラシアンの概念を使用して、スペクトル埋め込みはデータの低次元表現を求め、局所的な近傍情報を強調し、長距離情報を無視します。埋め込みは非線形ですが、埋め込み空間はユークリッドです。$U$ の固有ベクトルは埋め込み空間の点の座標を保持します（通常はプロット用に2次元または3次元、クラスタリング用にそれ以上）。スペクトル埋め込みは、低次元でのデータのプロット、クラスタリング、イメージング、分類、時間や他の次元にわたる軌跡の追跡などに使用されます。アプリケーションの例については、Ridrigues et *al.* (2018) [🎓](@ref) およびそこにある参考文献を参照してください。

**引数**:

  * $$
    Ω
    $$

    は [`laplacian`](@ref) 関数によって得られた実数 `LowerTriangular` 正規化ラプラシアンです。
  * $$
    q
    $$

    はラプラシアン固有マップの次元です。
  * 次のものはパワー反復のための *<オプションのキーワード引数>* です：
  * `tol` は収束のための許容誤差です（以下を参照）。
  * `maxiter` は許可される最大反復回数です。
  * `verbose` が true の場合、すべての反復での収束が印刷されます。

!!! note "Nota Bene"
    要求できる最大の $q$ の値は $n-1$ で、ここで $n$ はラプラシアンのサイズです。一般に、$q=2$ または $q=3$ が要求されます。

    $$
    tol
    $$

    は $Ω$ の（実数）型の `Base.eps` の平方根にデフォルト設定されています。これは、約半分の有効数字の2回の連続したパワー反復にわたる収束基準の等価性を要求することに対応します。


**関連項目**: [`distanceSqrMat`](@ref), [`laplacian`](@ref), [`spectralEmbedding`](@ref).

**例**

```julia
using PosDefManifold
# 4つのランダムな10x10 SPD行列のセットを生成
Pset=randP(10, 4)
Δ²=distanceSqrMat(Fisher, Pset)
Ω=laplacian(Δ²)
evalues, maps, iterations, convergence=laplacianEM(Ω, 2)
evalues, maps, iterations, convergence=laplacianEM(Ω, 2; verbose=true)
evalues, maps, iterations, convergence=laplacianEM(Ω, 2; verbose=true, maxiter=500)
```
