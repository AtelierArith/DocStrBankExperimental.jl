`Scale(α::Number,A::AbstractOperator)`

Shorthand constructor: 

`*(α::Number,A::AbstractOperator)` 

Scale an `AbstractOperator` by a factor of `α`.

```julia
julia> A = FiniteDiff((10,2))
δx  ℝ^(10, 2) -> ℝ^(9, 2)

julia> S = Scale(10,A)
αδx  ℝ^(10, 2) -> ℝ^(9, 2)

julia> 10*A         #shorthand 
αℱc  ℝ^10 -> ℝ^10

```
