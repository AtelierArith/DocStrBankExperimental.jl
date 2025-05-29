```
def_space_coord(nc::NCDataset, space::Spaces.AbstractSpace; type = "dgll")
```

NetCDFデータセット`nc`に対して、[`remap_weights`](@ref)で使用されるタイプと互換性のある`space`の空間次元を追加します。

互換性のある次元がすでに存在する場合、それは再利用されます。
