```
experiments(x)
```

`MultiAssayExperiment` `x` に含まれるすべての実験を含む順序付き辞書を返します。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> collect(keys(experiments(x)))
2-element Vector{String}:
 "foo"
 "bar"
```
