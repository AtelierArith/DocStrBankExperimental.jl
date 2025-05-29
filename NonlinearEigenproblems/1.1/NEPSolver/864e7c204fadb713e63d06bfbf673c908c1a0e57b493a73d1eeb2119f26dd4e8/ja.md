```
λv,V=contour_beyn([eltype,] nep [,mintegrator];[tol,][logger,][σ,][radius,][linsolvercreator,][N,][neigs,][k])
```

この関数は、`σ`を中心とし、`radius`で与えられた半径を持つ楕円を使用して、Beynの輪郭積分アプローチを用いて固有値を計算します。もし`radius`が1つだけ与えられた場合、輪郭は円になります。数値積分法は、デフォルトで`MatrixTrapezoidal`の`MatrixIntegrator`から継承された型である`mintegrator`で指定されます。積分器の並列実装を使用するには、`MatrixTrapezoidalParallel`を使用します。整数`k`はプローブ部分空間のサイズを指定します。`N`は積分するための点の数に対応します。楕円のみがサポートされている輪郭です。`linsolvercreator`は、ベクトルだけでなく（長方形の）行列を右辺として処理できるlinsolverを作成する必要があります。複素数演算で積分するため、`eltype`は複素型でなければなりません。

kwargs `neigs`は、求める固有値の数を指定し、`k`は積分される行列の列数です（デフォルトは`k=neigs+1`）。`k`パラメータを指定し、`neigs=typemax(Int)`を設定すると、見つかったすべての固有値が返されます。kwarg `sanity_check`は、固有対のソートとチェック（および削除）を行うかどうかを決定します。無効にすると、メソッドは`k`（潜在的に不正確な）固有対を返します。パラメータ`errmeasure`、`tol`、および`rank_drop_tol`は、正確な固有値を抽出するためのサニティチェックに使用されます。

# 例

```julia-repl
julia> using LinearAlgebra
julia> nep=nep_gallery("dep0");
julia> # 単位円内で2つの固有値を探す
julia> λv,V=contour_beyn(nep,radius=1.1,neigs=3);
julia> norm(compute_Mlincomb(nep,λv[1],V[:,1])) # 固有対 1
1.7462847531404259e-15
julia> norm(compute_Mlincomb(nep,λv[2],V[:,2])) # 固有対 2
7.69695692032292e-15
```

# 参考文献

  * Wolf-Jürgen Beyn, 非線形固有値問題を解くための積分法, Linear Algebra and its Applications 436 (2012) 3839–3863
