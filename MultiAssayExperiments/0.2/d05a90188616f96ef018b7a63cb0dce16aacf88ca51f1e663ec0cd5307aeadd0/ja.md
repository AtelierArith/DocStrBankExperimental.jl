```
setexperiments!(x, value)
```

`MultiAssayExperiment` `x` の実験を `OrderedDict` `value` に設定します。これにより、変更された `x` への参照が返されます。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> y = copy(experiments(x));

julia> delete!(y, "foo");

julia> setexperiments!(x, y);

julia> collect(keys(experiments(x)))
1-element Vector{String}:
 "bar"
```
