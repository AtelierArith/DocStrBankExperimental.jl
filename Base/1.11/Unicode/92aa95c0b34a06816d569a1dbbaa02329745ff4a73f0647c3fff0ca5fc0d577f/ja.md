```
lowercase(s::AbstractString)
```

`s`のすべての文字を小文字に変換して返します。

関連情報としては、[`uppercase`](@ref)、[`titlecase`](@ref)、[`lowercasefirst`](@ref)があります。

# 例

```jldoctest
julia> lowercase("STRINGS AND THINGS")
"strings and things"
```
