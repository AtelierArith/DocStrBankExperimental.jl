`ZeroPad([domainType::Type,] dim_in::Tuple, zp::Tuple)`

`ZeroPad(x::AbstractArray, zp::Tuple)`

サイズ `dim_in` の配列 `x` に掛けられると、サイズ `dim_in .+ zp` の拡張配列 `y` を返す `LinearOperator` を作成します。ここで、`y[1:dim_in[1], 1:dim_in[2] ... ] = x` であり、他の場所はゼロです。

```julia
julia> Z = ZeroPad((2,2),(0,2))
[I;0]  ℝ^(2, 2) -> ℝ^(2, 4)

julia> Z*ones(2,2)
2×4 Array{Float64,2}:
 1.0  1.0  0.0  0.0
 1.0  1.0  0.0  0.0

```
