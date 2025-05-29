```
metadata(x)
```

`MultiAssayExperiment` `x` からメタデータを含む辞書を返します。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> collect(keys(metadata(x)))
1-element Vector{String}:
 "version"
```
