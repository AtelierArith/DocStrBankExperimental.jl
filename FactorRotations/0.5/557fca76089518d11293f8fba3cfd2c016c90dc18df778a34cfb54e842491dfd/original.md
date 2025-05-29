```
criterion_and_gradient!(∇Q::Union{AbstractMatrix{<:Real}, Nothing},
                        method::RotationMethod, Λ::AbstractMatrix{<:Real})
```

Calculate the quality criterion *Q* and its gradient for a given `method` with respect to the factor loading matrix `Λ`. The gradient is output into `∇Q` matrix, which should have the same dimensions as `Λ`. The `∇Q` calculation is skipped if `∇Q ≡ nothing`.

Returns the *Q* criterion value.
