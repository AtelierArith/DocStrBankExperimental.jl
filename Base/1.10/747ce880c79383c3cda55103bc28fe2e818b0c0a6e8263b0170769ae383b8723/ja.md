```
chomp(s::AbstractString) -> SubString
```

文字列から単一の末尾改行を削除します。

関連項目は [`chop`](@ref) です。

# 例

```jldoctest
julia> chomp("Hello\n")
"Hello"
```
