```
brick(n::NTuple{3, Integer}, p::NTuple{3, Bool}=(false, false, false))
```

新しい [`Connectivity`](@ref) を返します。これは、`n[1]`-by-`n[2]`-by-`n[3]` の長方形のオクトリーメッシュです。ブロックは、`p[1]`、`p[2]`、および `p[3]` がそれぞれ `true` の場合、x、y、および z で周期的です。
