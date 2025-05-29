```
var = getindex(ds::Union{AbstractDataset,AbstractVariable},cfname::CFStdName)
```

データセットから標準名 `cfname` を持つNetCDF変数 `var` を返します。最初の引数が変数である場合、検索は同じ次元名を持つすべての変数に制限されます。
