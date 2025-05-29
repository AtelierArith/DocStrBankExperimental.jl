```
gather(data, new_name_old_names...)
```

各 `new_name, old_names` ペアに対して、`old_names` を単一の `new_name` にまとめます。 [`spread`](@ref) の逆です。

```jldoctest
julia> using LightQuery


julia> using Test: @inferred


julia> data = (a = 1, b = 1.0, c = 1, d = 1.0, e = 1, f = 1.0);


julia> @inferred gather(data, g = (name"b", name"e"), h = (name"c", name"f"))
(a = 1, d = 1.0, g = (b = 1.0, e = 1), h = (c = 1, f = 1.0))
```
