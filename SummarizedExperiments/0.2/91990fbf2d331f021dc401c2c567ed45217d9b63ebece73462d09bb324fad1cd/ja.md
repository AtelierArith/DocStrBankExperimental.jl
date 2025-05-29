```
metadata(x)
```

`x`からメタデータを`Dict`として返します。キーはメタデータフィールド名です。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> metadata(x)
Dict{String, Any} with 1 entry:
  "version" => "1.1.0"
```
