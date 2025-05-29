```
get_decorations(str::AbstractString) -> String
```

`str`内の装飾を含む文字列を返します。

# 拡張ヘルプ

## 例

```julia
julia> get_decorations("This is a \e[1mbold string\e[45mwith a different background\e[0m.")
"\e[1m\e[45m\e[0m"
```
