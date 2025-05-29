```
contour_block_SS([eltype,] nep [,mintegrator];[tol,][logger,][σ,][radius,][linsolvercreator,][N,][neigs,][k,][L])
```

これは、高次モーメントの計算に基づく block_SS コンター積分法の実装です。コンターは `σ` を中心とした楕円で、`radius` で与えられた半径を持ち、もし `radius` が1つだけ与えられた場合、コンターは円になります。数値積分法は `mintegrator` で指定され、これは `MatrixIntegrator` から継承された型で、デフォルトは `MatrixTrapezoidal` です。積分器の並列実装を使用するには `MatrixTrapezoidalParallel` を使用します。整数 `k` はプローブ部分空間のサイズを指定します。`N` は積分点の数に対応します。整数 L はモーメントの数を指定します。楕円のみがサポートされているコンターです。`linsolvercreator` は、ベクトルだけでなく（長方形の）行列を右辺として処理できるリニアソルバーを作成する必要があります。複素数演算で積分するため、`eltype` は複素型でなければなりません。

# 例

```julia-repl
julia> nep=SPMF_NEP([[0 1 ; 1 1.0], [1 0 ; 0 0]], [s->one(s),s->exp(1im*s^2)]);
julia> λ,V=contour_assu(nep,radius=3,neigs=6)
julia> @show λ
6-element Array{Complex{Float64},1}:
  4.496403249731884e-15 + 2.506628274630998im
        -2.506628274631 - 2.8727020762175925e-15im
  3.219972424519104e-16 - 2.5066282746310034im
     2.5066282746310096 - 1.1438072192922029e-15im
 -2.3814273710772784e-7 - 7.748469160458366e-8im
   2.381427350935646e-7 + 7.748467479992284e-8im
```

# 参考文献

  * Asakura, Sakurai, Tadano, Ikegami, Kimura, コンター積分を用いた非線形固有値問題のための数値法, JSIAM Letters, 2009 Volume 1 Pages 52-55
  * Van Beeumen, Meerbergen, Michiels. 固有値問題に対するコンター積分と有理Krylov法の関係, 2016, TW673, https://lirias.kuleuven.be/retrieve/415487/

```
