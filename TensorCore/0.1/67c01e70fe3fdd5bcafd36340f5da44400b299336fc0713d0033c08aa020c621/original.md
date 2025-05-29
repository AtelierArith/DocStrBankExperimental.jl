```
hadamard(a, b)
a ⊙ b
```

For arrays `a` and `b`, perform elementwise multiplication. `a` and `b` must have identical `axes`.

`⊙` can be passed as an operator to higher-order functions.

# Examples

```jldoctest; setup=:(using TensorCore)
julia> a = [2, 3]; b = [5, 7];

julia> a ⊙ b
2-element Array{Int64,1}:
 10
 21

julia> a ⊙ [5]
ERROR: DimensionMismatch("Axes of `A` and `B` must match, got (Base.OneTo(2),) and (Base.OneTo(1),)")
[...]
```

See also `hadamard!(y, a, b)`.
