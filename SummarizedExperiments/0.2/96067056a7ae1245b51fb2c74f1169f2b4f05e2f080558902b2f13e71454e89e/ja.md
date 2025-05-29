```
setmetadata!(x, value)
```

`x`のメタデータを`value`に設定します。`value`はメタデータフィールド名のキーを持つ`Dict`です。

# 例

```jldoctest
julia> using SummarizedExperiments

julia> x = exampleobject(20, 10);

julia> setmetadata!(x, Dict{String,Any}("foo" => 200));

julia> metadata(x)
Dict{String, Any} with 1 entry:
  "foo" => 200
```
