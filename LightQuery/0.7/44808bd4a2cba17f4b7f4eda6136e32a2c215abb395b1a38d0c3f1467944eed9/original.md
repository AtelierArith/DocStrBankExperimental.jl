```
spread(data, some_names...)
```

Unnest nested named tuples. Inverse of [`gather`](@ref).

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> gathered = (a = 1, d = 1.0, g = (b = 1.0, e = 1), h = (c = 1, f = 1.0));


julia> @inferred spread(gathered, name"g", name"h")
(a = 1, d = 1.0, b = 1.0, e = 1, c = 1, f = 1.0)
```
