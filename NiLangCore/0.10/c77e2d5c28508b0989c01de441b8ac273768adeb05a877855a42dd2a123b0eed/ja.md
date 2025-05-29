```
@code_reverse ex
```

`ex`の逆の式を取得します。

```jldoctest; setup=:(using NiLangCore)
julia> @code_reverse x += exp(3.0)
:(x -= exp(3.0))
```
