```
try_next!(reader::PAFReader) -> Union{Nothing, PAFRecord, ParserException}
```

[`PAFReader`](@ref) からレコードを読み取ろうとし、リーダーを進めます。これにより、次の3つのオプションのいずれかが得られます：

  * リーダーが空の場合、`nothing` を返し、リーダーを進めません
  * 次のレコードが無効な場合、`ParserException` を返し（スローせずに）、リーダーを進めません
  * 次のレコードが有効な場合、それを [`PAFRecord`](@ref) として返し、リーダーを進めます

リーダー自体が進まなくても、内部バッファを埋めることがあり、ラップしている `IO` オブジェクトを進めることがあります。

# 例

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
