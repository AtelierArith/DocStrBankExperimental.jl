```
iscuda(c::Ceed)
```

与えられた [`Ceed`](@ref) オブジェクトがリソース `"/gpu/cuda/*"` を持っている場合は true を返し、それ以外の場合は false を返します。
