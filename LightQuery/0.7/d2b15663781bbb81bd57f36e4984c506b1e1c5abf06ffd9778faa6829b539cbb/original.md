```
rename(data, new_name_old_names...)
```

Rename `data`.

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> data = (a = 1, b = 1.0, c = 1, d = 1.0, e = 1, f = 1.0);


julia> @inferred rename(data, c2 = name"c", f2 = name"f")
(a = 1, b = 1.0, d = 1.0, e = 1, c2 = 1, f2 = 1.0)
```
