```
coldata(x, check = true)
```

列の注釈を、`x`の列数と同じ行数を持つ`DataFrame`として返します。最初の列は`"name"`と呼ばれ、`x`の列名を含みます。これは`Vector{String}`または`Vector{Nothing}`（列名が利用できない場合）である可能性があります。

`check = true`の場合、この関数は返される`DataFrame`に対する期待が満たされていることを確認します。失敗があれば警告が発生します。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> names(coldata(x))
3-element Vector{String}:
 "name"
 "Treatment"
 "Response"

julia> size(coldata(x))
(10, 3)
```
