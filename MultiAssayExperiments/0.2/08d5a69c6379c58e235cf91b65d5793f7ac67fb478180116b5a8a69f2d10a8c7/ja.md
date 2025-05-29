```
setmetadata!(x, value)
```

`MultiAssayExperiment` `x` のメタデータを辞書 `value` に設定します。これにより、変更された `x` への参照が返されます。

# 例

```jldoctest
julia> using MultiAssayExperiments

julia> x = MultiAssayExperiments.exampleobject();

julia> meta = copy(metadata(x));

julia> meta["version"] = "0.2.0";

julia> setmetadata!(x, meta);

julia> metadata(x)["version"]
"0.2.0"
```
