```
Sequence{T<:VectorSpace,S<:AbstractVector}
```

Compactly supported sequence in the given space.

Fields:

  * `space :: T`
  * `coefficients :: S`

Constructors:

  * `Sequence(::VectorSpace, ::AbstractVector)`
  * `Sequence(coefficients::AbstractVector)`: equivalent to `Sequence(ParameterSpace()^length(coefficients), coefficients)`

# Examples

```jldoctest
julia> Sequence(Taylor(2), [1, 2, 1]) # 1 + 2x + x^2
Sequence in Taylor(2) with coefficients Vector{Int64}:
 1
 2
 1

julia> Sequence(Taylor(1) ⊗ Fourier(1, 1.0), [0.5, 0.5, 0.0, 0.0, 0.5, 0.5]) # (1 + x) cos(y)
Sequence in Taylor(1) ⊗ Fourier(1, 1.0) with coefficients Vector{Float64}:
 0.5
 0.5
 0.0
 0.0
 0.5
 0.5

julia> Sequence([1, 2, 3])
Sequence in 𝕂³ with coefficients Vector{Int64}:
 1
 2
 3
```
