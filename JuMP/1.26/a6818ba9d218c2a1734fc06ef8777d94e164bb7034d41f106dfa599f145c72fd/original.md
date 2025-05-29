```
print_active_bridges(
    [io::IO = stdout,]
    model::GenericModel,
    F::Type,
    S::Type{<:MOI.AbstractSet},
)
```

Print a list of bridges required for a constraint of type `F`-in-`S`.
