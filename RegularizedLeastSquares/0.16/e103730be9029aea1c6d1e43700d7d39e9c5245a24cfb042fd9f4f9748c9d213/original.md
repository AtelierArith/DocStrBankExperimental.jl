```
MaskedRegularization
```

Nested regularization term that only applies `prox!` and `norm` to elements of `x` for which the mask is `true`.

# Examples

```julia
julia> positive = PositiveRegularization();

julia> masked = MaskedRegularization(reg, [true, false, true, false]);

julia> prox!(masked, fill(-1, 4))
4-element Vector{Float64}:
  0.0
 -1.0
  0.0
 -1.0
```
