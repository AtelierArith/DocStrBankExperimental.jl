```
assay(x[, i]; check = true)
```

`x`の要求されたアッセイを返します。`i`はインデックスを指定する整数または名前を含む文字列である可能性があります。`i`が指定されていない場合、最初のアッセイが返されます。

返されるアッセイは、最初の2次元に対して`x`と同じ範囲を持つ必要があります。`check = true`の場合、この関数はこの期待が満たされていることを確認します。失敗があった場合は警告が発生します。

# 例

```jldoclist
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

# これらはすべて同じ値を返します。
julia> assay(x);

julia> assay(x, 1);

julia> assay(x, "foo");
```
