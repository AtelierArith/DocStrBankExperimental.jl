```
gilbertindices(dims::Tuple{Int,Int}; majdim=dims[1] >= dims[2] ? 1 : 2)
```

`CartesianIndex` オブジェクトのベクトルを構築し、一般化されたヒルベルト空間充填によって順序付けられ、`CartesianIndex(1,1)` から始まります。 `majdim==1` の場合は `CartesianIndex(dims[1],1)` で終了し、`majdim==2` の場合は `CartesianIndex(1,dims[2])` で終了します（または最も近い実行可能な点）。
