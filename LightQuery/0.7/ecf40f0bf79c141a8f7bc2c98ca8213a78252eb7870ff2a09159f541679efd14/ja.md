```
transform(data, assignments...)
```

`assignments`を`data`にマージし、古い値を上書きします。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> data = (a = 1, b = 1.0, c = 1, d = 1.0, e = 1, f = 1.0);


julia> @inferred transform(data, c = 2.0, f = 2, g = 1, h = 1.0)
(a = 1, b = 1.0, d = 1.0, e = 1, c = 2.0, f = 2, g = 1, h = 1.0)
```
