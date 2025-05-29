```
size(x::SummarizedExperiment)
```

`x`の行数と列数を含む2タプルを返します。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> size(x)
(20, 10)
```
