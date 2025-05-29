```
SystemModel(filename::String)
```

適切にフォーマットされたHDF5ファイルから`SystemModel`をロードします。これらのファイルは通常、.prasファイル名拡張子を持っています。

# 例

```julia
sys = SystemModel("path/to/prasfile.pras")
```
