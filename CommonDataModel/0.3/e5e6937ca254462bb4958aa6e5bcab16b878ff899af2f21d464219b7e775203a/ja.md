```
CommonDatamodel.dimnames(ds::AbstractDataset)
```

`ds`のすべての次元名のイテラブルを返します。この情報は、プロパティ`ds.dim`を使用してもアクセスできます：

# 例

```julia
ds = NCDataset("results.nc", "r");
dimnames = keys(ds.dim)
```
