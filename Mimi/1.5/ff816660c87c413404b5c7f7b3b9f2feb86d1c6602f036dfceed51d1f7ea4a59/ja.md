```
hasvalue(arr::TimestepArray, ts::VariableTimestep, idxs::Int...)
```

`true` または `false` を返します。`true` は、TimestepArray `arr` がインデックス `idxs` 内に Timestep `ts` を含む場合です。Array と Timestep が異なる TIMES を持つ場合に使用され、すべての次元を検証します。
