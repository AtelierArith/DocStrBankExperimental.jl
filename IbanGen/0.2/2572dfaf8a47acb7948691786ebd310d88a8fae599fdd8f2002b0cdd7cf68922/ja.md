```
is_supported_country(country_code)::Bool
```

`country_code`で識別される国がサポートされているかどうかを示すブール値を返します。

# 例

```julia
julia> is_supported_country("DE")
true

julia> is_supported_country("ZZ")
false
```
