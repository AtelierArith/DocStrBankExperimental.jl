`Variation([domainType=Float64::Type,] dim_in::Tuple)`

`Variation(dims...)`

`Variation(x::AbstractArray)`

配列 `x::AbstractArray{N}` に対して掛け算を行うと、`i` 番目の `direction` に沿った前方有限差分を使用して得られたベクトル化された離散勾配からなる `i` 番目の列を持つ行列を返す `LinearOperator` を作成します。

```julia
julia> Variation(Float64,(10,2))
Ʋ  ℝ^(10, 2) -> ℝ^(20, 2)

julia> Variation(2,2,2)
Ʋ  ℝ^(2, 2, 2) -> ℝ^(8, 3)

julia> Variation(ones(2,2))*[1. 2.; 1. 2.]
4×2 Array{Float64,2}:
 0.0  1.0
 0.0  1.0
 0.0  1.0
 0.0  1.0

```
