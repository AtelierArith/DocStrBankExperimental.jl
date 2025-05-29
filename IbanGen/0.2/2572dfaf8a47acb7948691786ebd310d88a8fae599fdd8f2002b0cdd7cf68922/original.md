```
is_supported_country(country_code)::Bool
```

Return a boolean indicating if the country identified by `country_code` is supported.

# Examples

```julia
julia> is_supported_country("DE")
true

julia> is_supported_country("ZZ")
false
```
