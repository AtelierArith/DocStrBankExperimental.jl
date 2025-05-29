`IDFT([domainType=Float64::Type,] dim_in::Tuple [,dims])`

`IDFT(dim_in...)`

`IDFT(x::AbstractArray [,dims])`

配列 `x::AbstractArray{N}` に掛け算されると、次元 `dims` の `x` に対して `N` 次元の逆離散フーリエ変換を返す `LinearOperator` を作成します。

```julia
julia> IDFT(Complex{Float64},(10,10))
ℱ⁻¹  ℂ^(10, 10) -> ℂ^(10, 10)

julia> IDFT(10,10)
ℱ⁻¹ ℝ^(10, 10) -> ℂ^(10, 10)

julia> A = IDFT(ones(3))
ℱ⁻¹  ℝ^3 -> ℂ^3

julia> A*ones(3)
3-element Array{Complex{Float64},1}:
 1.0+0.0im
 0.0+0.0im
 0.0+0.0im
```
