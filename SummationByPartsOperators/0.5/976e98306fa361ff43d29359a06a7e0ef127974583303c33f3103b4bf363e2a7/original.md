```
xmax(D)
```

Return the right boundary `xmax` of the domain specified when constructing the derivative operator `D`. Note that this might be different from the rightmost node of the [`grid`](@ref) of `D` when not all boundary nodes are included, e.g., for periodic derivative operators.
