```
lowercase(c::AbstractChar)
```

`c`を小文字に変換します。

参照してください [`uppercase`](@ref), [`titlecase`](@ref).

# 例

```jldoctest
julia> lowercase('A')
'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)

julia> lowercase('Ö')
'ö': Unicode U+00F6 (category Ll: Letter, lowercase)
```
