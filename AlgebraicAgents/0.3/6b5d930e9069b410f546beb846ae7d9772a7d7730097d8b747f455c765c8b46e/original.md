```
f"query"
```

Turn a query string into a query instance, see also [`FilterQuery`](@ref).

Supports string interpolations.

# Examples

```julia
filter(agents, f"_.age > 1 && _.name ∈ ['a', 'b']")
i = 1; filter(agents, f"_.age > $i && _.name ∈ ['a', 'b']")
```
