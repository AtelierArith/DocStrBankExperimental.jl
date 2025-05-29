`DFT([domainType=Float64::Type,] dim_in::Tuple [,dims])`

`DFT(dim_in...)`

`DFT(x::AbstractArray [,dims])`

配列 `x::AbstractArray{N}` に掛け算されると、次元 `dims` の `x` に対する `N` 次元離散フーリエ変換を返す `LinearOperator` を作成します。

```julia
julia> DFT(Complex{Float64},(10,10))
ℱ  ℂ^(10, 10) -> ℂ^(10, 10)

julia> DFT(10,10)
ℱ  ℝ^(10, 10) -> ℂ^(10, 10)

julia> A = DFT(ones(3))
ℱ  ℝ^3 -> ℂ^3

julia> A*ones(3)
3-element Array{Complex{Float64},1}:
 3.0+0.0im
 0.0+0.0im
 0.0+0.0im
```
