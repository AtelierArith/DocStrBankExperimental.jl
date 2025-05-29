```
voxelreuse(trainimg::AbstractArray{T,N}, tilesize::Dims{N};
           overlap::NTuple{N,Float64}=ntuple(i->1/6,N),
           nreal::Integer=10, kwargs...)
```

返されるのは、平均ボクセル再利用率 `[0,1]` とその標準偏差です。

### 注意事項

  * `nreal` を大きくするほど近似が良くなります。
  * キーワード引数 `kwargs` は直接 `iqsim` に渡されます。
