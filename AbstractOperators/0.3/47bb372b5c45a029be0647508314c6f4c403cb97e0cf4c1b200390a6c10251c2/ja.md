`IDCT([domainType=Float64::Type,] dim_in::Tuple)`

`IDCT(dim_in...)`

`IDCT(x::AbstractArray)`

配列 `x::AbstractArray{N}` に掛け算されると、`x` の `N` 次元離散コサイン変換を返す `LinearOperator` を作成します。

```julia
julia> IDCT(Complex{Float64},(10,10))
ℱc⁻¹  ℂ^(10, 10) -> ℂ^(10, 10) 

julia> IDCT(10,10)
ℱc⁻¹  ℝ^(10, 10) -> ℂ^(10, 10) 

julia> A = IDCT(ones(3))
ℱc⁻¹  ℝ^3 -> ℝ^3

julia> A*[1.;0.;0.]
3-element Array{Float64,1}:
 0.57735
 0.57735
 0.57735

```
