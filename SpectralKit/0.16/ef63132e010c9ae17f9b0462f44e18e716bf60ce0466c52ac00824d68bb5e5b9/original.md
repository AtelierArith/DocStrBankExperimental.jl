```julia
∂(I)

```

Partial derivatives along the given coordinates.

!!! NOTE     Partial derivatives are currently **experimental** and not heavily tested. API may     change at any point without prior notice or deprecation.

The following are equivalent, and represent $\partial_1 \partial^2_2$, ie the first derivative along the first axis, and the second partial derivative along the second axis.

```@jldoctest
julia> ∂(1, 2)
∂(1, 2)

julia> ∂((1, 2))
∂(1, 2)
```

Only the vararg form allows trailing zeros, which are stripped:

```@jldoctest
julia> ∂(1, 0)
∂(1)

julia> ∂((1, 0))
ERROR: ArgumentError: I ≡ () || last(I) ≠ 0 must hold.
```

Use the empty form for no derivatives:

```@jldoctest
julia> ∂()
∂()
```

Combine derivatives using `union` or `∪`:

```jldoctest
julia> ∂(1, 2) ∪ ∂(2, 1)
union(∂(2, 1), ∂(1, 2))
```
