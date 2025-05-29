```
LinearOperator{T<:VectorSpace,S<:VectorSpace,R<:AbstractMatrix}
```

Compactly supported linear operator with effective domain and codomain.

Fields:

  * `domain :: T`
  * `codomain :: S`
  * `coefficients :: R`

Constructors:

  * `LinearOperator(::VectorSpace, ::VectorSpace, ::AbstractMatrix)`
  * `LinearOperator(coefficients::AbstractMatrix)`: equivalent to `LinearOperator(ParameterSpace()^size(coefficients, 2), ParameterSpace()^size(coefficients, 1), coefficients)`

# Examples

```jldoctest
julia> LinearOperator(Taylor(1), Taylor(1), [1 2 ; 3 4])
LinearOperator : Taylor(1) → Taylor(1) with coefficients Matrix{Int64}:
 1  2
 3  4

julia> LinearOperator(Taylor(2), ParameterSpace(), [1.0 0.5 0.25])
LinearOperator : Taylor(2) → 𝕂 with coefficients Matrix{Float64}:
 1.0  0.5  0.25

julia> LinearOperator([1 2 3 ; 4 5 6])
LinearOperator : 𝕂³ → 𝕂² with coefficients Matrix{Int64}:
 1  2  3
 4  5  6
```
