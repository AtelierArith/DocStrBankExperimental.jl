```
xmin(D)
```

Return the left boundary `xmin` of the domain specified when constructing the derivative operator `D`. Note that this might be different from the leftmost node of the [`grid`](@ref) of `D` when not all boundary nodes are included, e.g., for periodic derivative operators.
