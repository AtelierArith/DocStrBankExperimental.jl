```
@code_reverse ex
```

Get the reversed expression of `ex`.

```jldoctest; setup=:(using NiLangCore)
julia> @code_reverse x += exp(3.0)
:(x -= exp(3.0))
```
