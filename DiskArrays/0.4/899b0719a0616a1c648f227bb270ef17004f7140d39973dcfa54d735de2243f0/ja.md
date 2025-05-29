```
cache(A::AbstractArray; maxsize=1000, mmap=false)
```

内部ディスク配列を `CacheDiskArray` でラップします。

この関数は、YAXArrays.jl や Rasters.jl のように、その後ディスク配列を再ラップしたいパッケージによって拡張されることを意図しています。
