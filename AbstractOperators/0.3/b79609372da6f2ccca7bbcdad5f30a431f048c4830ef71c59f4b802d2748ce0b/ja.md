`BroadCast(A::AbstractOperator, dim_out...)`

`AbstractOperator`のコドメイン次元をブロードキャストします。

```julia
julia> A = Eye(2)
I  ℝ^2 -> ℝ^2

julia> B = BroadCast(A,(2,3))
.I  ℝ^2 -> ℝ^(2, 3)

julia> B*[1.;2.]
2×3 Array{Float64,2}:
 1.0  1.0  1.0
 2.0  2.0  2.0

```
