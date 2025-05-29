```
mid_point(M::AbstractManifold, p1, p2)
```

多様体 `M` の2点 `p1` と `p2` の中点を計算します。デフォルトでは [`log`](@ref) を使用し、ベクトルを2で割り、[`exp`](@ref) を使用します。
