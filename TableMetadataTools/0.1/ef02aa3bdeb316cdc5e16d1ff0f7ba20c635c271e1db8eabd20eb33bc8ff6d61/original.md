```
toml2meta!(table, toml::Union{AbstractString, IO})
```

Store table-level and column-level metadata represented in TOML and passed in `toml` to `table` (discarding all previously present metadata).

The funcion assumes that `toml` is a properly formatted TOML, typically previously generated by [`meta2toml`](@ref).

See also: [`meta2toml`](@ref)
