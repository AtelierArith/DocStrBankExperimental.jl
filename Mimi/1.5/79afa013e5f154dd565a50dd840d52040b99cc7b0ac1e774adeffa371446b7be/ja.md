```
hasvalue(arr::TimestepArray, ts::FixedTimestep, idxs::Int...)
```

`true` または `false` を返します。`true` は、TimestepArray `arr` がインデックス `idxs` 内に Timestep `ts` を含む場合です。Array と Timestep が異なる FIRST を持つ場合に使用され、すべての次元を検証します。
