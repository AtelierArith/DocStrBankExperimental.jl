```
try_parse(x) -> Union{PAFRecord, ParserException}
```

`x`を`PAFRecord`に解析しようとします。`x`は`String`や`Vector{UInt8}`など、`MemoryView`を実装している任意の型である可能性があります。

# 例

```jldoctest
julia> valid_line = open(readline, path_to_paf);

julia> typeof(PAF.try_parse(valid_line))
PAFRecord

julia> typeof(PAF.try_parse("invalid string"))
PairwiseMappingFormat.ParserException
```

関連情報: [`PAFRecord`](@ref), [`try_next!`](@ref)
