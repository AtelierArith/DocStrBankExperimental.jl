```
brick(n::NTuple{2, Integer}, p::NTuple{2, Bool}=(false, false))
```

新しい [`Connectivity`](@ref) を返します。これは、`n[1]`-by-`n[2]` の長方形のクワッドツリー接続性です。ブロックは、`p[1]` と `p[2]` がそれぞれ `true` の場合、x および y で周期的です。
