A callable that calculates the value and the derivative of the argument. Higher-order derivatives can be obtained by using an exponent, or multiplication.

```jldoctest
julia> 𝑑(2.0)
2.0 + 1.0⋅Δ

julia> (𝑑^3)(2.0)
2.0 + 1.0⋅Δ + 0.0⋅Δ² + 0.0⋅Δ³
```

Note that non-literal exponentiation requires `^Val(y)`, for type stability.

See [`linear_combination`](@ref) for examples of evaluating derivatives of basis functions and linear combinations.
