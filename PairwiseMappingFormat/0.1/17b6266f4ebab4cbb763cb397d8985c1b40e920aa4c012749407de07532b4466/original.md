```
try_next!(reader::PAFReader) -> Union{Nothing, PAFRecord, ParserException}
```

Try to read a record from the [`PAFReader`](@ref) and advance the reader. This may yield one of three options:

  * If the reader is empty, return `nothing` and do not advance the reader
  * If the next record is invalid, return (do not throw) a `ParserException` and do not advance the reader
  * If the next record is valid, return it as a [`PAFRecord`](@ref) and advance the reader

Even if the reader itself is not advanced, it may still fill its internal buffer, advancing the `IO` object it wraps.

# Examples

```jldoctest
julia> reader = PAFReader(open(path_to_paf));

julia> try_next!(reader) isa PAFRecord
true

julia> [try_next!(reader) for i in 1:2] isa Vector{PAFRecord}
true

julia> typeof([try_next!(reader) for i in 1:100])
Vector{Nothing} (alias for Array{Nothing, 1})

julia> close(reader); reader = PAFReader(IOBuffer("bad data"));

julia> try_next!(reader) isa PAF.ParserException
true

julia> all(i -> try_next!(reader) isa PAF.ParserException, 1:100)
true
```
