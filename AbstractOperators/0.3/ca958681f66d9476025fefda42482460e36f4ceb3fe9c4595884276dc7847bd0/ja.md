`FiniteDiff([domainType=Float64::Type,] dim_in::Tuple, direction = 1)`

`FiniteDiff(x::AbstractArray, direction = 1)`

指定された`direction`に対して前方有限差分を使用して得られた離散化された勾配を返す`LinearOperator`を作成します。これは、配列`x::AbstractArray{N}`と掛け算されると、結果を返します。

```julia
julia> FiniteDiff(Float64,(3,))
δx  ℝ^3 -> ℝ^2

julia> FiniteDiff((3,4),2)
δy  ℝ^(3, 4) -> ℝ^(3, 3)

julia> all(FiniteDiff(ones(2,2,2,3),1)*ones(2,2,2,3) .== 0)
true

```
