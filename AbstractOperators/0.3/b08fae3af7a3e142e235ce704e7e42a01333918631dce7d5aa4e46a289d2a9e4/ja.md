`DCT([domainType=Float64::Type,] dim_in::Tuple)`

`DCT(dim_in...)`

`DCT(x::AbstractArray)`

配列 `x::AbstractArray{N}` と掛け算をすると、`x` の `N` 次元逆離散コサイン変換を返す `LinearOperator` を作成します。

```julia
julia> DCT(Complex{Float64},(10,10))
ℱc  ℂ^(10, 10) -> ℂ^(10, 10) 

julia> DCT(10,10)
ℱc  ℝ^(10, 10) -> ℂ^(10, 10) 

julia> A = DCT(ones(3))
ℱc  ℝ^3 -> ℝ^3

julia> A*ones(3)
3-element Array{Float64,1}:
 1.73205
 0.0
 0.0

```
