```
remove(data, old_names...)
```

Remove `old_names` from `data`.

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> data = (a = 1, b = 1.0, c = 1, d = 1.0, e = 1, f = 1.0);


julia> @inferred remove(data, name"c", name"f")
(a = 1, b = 1.0, d = 1.0, e = 1)
```
