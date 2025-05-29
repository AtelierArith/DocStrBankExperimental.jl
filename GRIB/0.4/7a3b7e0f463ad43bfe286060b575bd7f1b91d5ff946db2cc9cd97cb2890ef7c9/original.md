```
select!(index::Index, key::AbstractString, value::AbstractString)
select!(index::Index, key::AbstractString, value::AbstractFloat)
select!(index::Index, key::AbstractString, value::AbstractFloat)
```

Reduce the size of the index to messages that match the key-value pair.

# Examples

```Julia
Index(filename, "shortName") do index
    select!(index, "shortName", "tp")
    # Index now only has messages about total precipitation
end

Index(filename, "level") do index
    select!(index, "level", 850)
    # Index now only has messages at level 850
end
```
