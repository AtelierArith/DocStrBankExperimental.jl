```
ParserException
```

The exception type thrown by iterating [`PAFReader`](@ref), or a failed `parse` of a [`PAFRecord`](@ref). The functions `try_parse` and `try_next!` may return (not throw) values of this type. The line the error occurred may be accessed with the `.line` field. The error kind may be accessed with the `.kind` field.

# Examples

```jldoctest
julia> err = PAF.try_parse("abc");

julia> err.line
1

julia> print(err.kind)
TooFewFields
```
