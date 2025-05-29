```
rowdata(x; check = true)
```

行の注釈を `DataFrame` として返し、行数は `x` の行数と等しくなります。最初の列は `"name"` と呼ばれ、`x` の行名を含みます。これは `AbstractVector{AbstractString}` または `Vector{Nothing}`（行名が利用できない場合）である可能性があります。

`check = true` の場合、この関数は返される `DataFrame` が上記の期待を満たしていることを確認します。失敗があれば警告が発生します。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> names(rowdata(x))
2-element Vector{String}:
 "name"
 "Type"

julia> size(rowdata(x))
(20, 2)
```
