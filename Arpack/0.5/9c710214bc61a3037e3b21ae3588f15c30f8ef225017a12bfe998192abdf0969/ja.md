```
eigs(A; nev=6, ncv=max(20,2*nev+1), which=:LM, tol=0.0, maxiter=300, sigma=nothing, ritzvec=true, explicittransform=:auto, v0=zeros((0,)), check=0) -> (d,[v,],nconv,niter,nmult,resid)
```

行列 `A` の固有値 `d` を計算します。これは、実対称行列または一般的な非対称行列に対して、それぞれ暗黙的に再起動されたランチョス法またはアーノルディ法を使用します。詳細については [the manual](@ref man-eigs) を参照してください。

`eigs` は、要求された `nev` の固有値を `d` に、対応するリッツベクトル `v` （`ritzvec=true` の場合のみ）、収束した固有値の数 `nconv`、反復回数 `niter`、行列ベクトルの乗算回数 `nmult`、および最終残差ベクトル `resid` を返します。パラメータ `explicittransform` は、シフトと反転をジュリアコードで明示的に呼び出すかどうかを指定する `:auto`、`:none`、または `:shiftinvert` の値を取ります。

`check = 0` の場合、最大反復回数が超過した場合にエラーが発生します（`info = 1`）。これは通常、ARPACKマニュアルに従ってすべての可能な固有値が見つかったことを意味します。`check = 1` の場合、`info = 1` のときに現在収束した固有値を返します。そして `@warn` が表示されます。`check = 2` の場合、`info = 1` のときに現在収束した固有値を返します。

# 例

```jldoctest
julia> using LinearAlgebra, Arpack

julia> A = Diagonal(1:4);

julia> λ, ϕ = eigs(A, nev = 2);

julia> λ
2-element Array{Float64,1}:
 3.9999999999999996
 3.000000000000001
```
