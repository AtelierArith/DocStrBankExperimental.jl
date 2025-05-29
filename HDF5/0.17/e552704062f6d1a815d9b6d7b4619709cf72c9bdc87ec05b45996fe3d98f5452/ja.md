```
dataspace(dims::Tuple; max_dims::Tuple=dims)
dataspace(dims::Tuple, max_dims::Tuple)
```

与えられた次元 `dims` のためのシンプルな `Dataspace` を構築します。最大次元 `maxdims` は最大の可能なサイズを指定します：`-1` は無制限の次元を示すために使用できます。
