```
print_active_bridges(
    [io::IO = stdout,]
    model::GenericModel,
    S::Type{<:MOI.AbstractSet},
)
```

Print a list of bridges required to add a variable constrained to the set `S`.
