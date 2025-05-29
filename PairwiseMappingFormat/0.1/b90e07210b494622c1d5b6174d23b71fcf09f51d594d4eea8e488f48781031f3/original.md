```
try_parse(x) -> Union{PAFRecord, ParserException}
```

Try parsing `x` into a `PAFRecord`. `x` may be any type that implements `MemoryView`, such as `String` or `Vector{UInt8}`.

# Examples

```jldoctest
julia> valid_line = open(readline, path_to_paf);

julia> typeof(PAF.try_parse(valid_line))
PAFRecord

julia> typeof(PAF.try_parse("invalid string"))
PairwiseMappingFormat.ParserException
```

See also: [`PAFRecord`](@ref), [`try_next!`](@ref)
