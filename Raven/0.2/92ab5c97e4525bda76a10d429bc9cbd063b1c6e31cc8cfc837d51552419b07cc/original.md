```
flatten(obj, use=Real)
```

Flattens a hierarchical type to a tuple with elements of type `use`.

# Examples

```jldoctest
julia> flatten((a=(Complex(1, 2), 3), b=4))
(1, 2, 3, 4)

```

To convert the tuple to a vector, simply use [flatten(x)...], or using static arrays to avoid allocations: `SVector(flatten(x))`.
