```
assays(x; check = true)
```

`x` からすべてのアッセイを `OrderedDict` として返します。ここで、キーはアッセイ名です。返される各アッセイは、最初の2次元に対して `x` と同じ範囲を持つ必要があります。`check = true` の場合、この関数はこの期待が満たされていることを確認します。失敗があった場合は、警告が発生します。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> collect(keys(assays(x)))
3-element Vector{String}:
 "foo"
 "bar"
 "whee"
```
