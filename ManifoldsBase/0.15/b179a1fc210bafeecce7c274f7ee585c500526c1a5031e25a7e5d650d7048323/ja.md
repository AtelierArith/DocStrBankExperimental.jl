```
mid_point!(M::AbstractManifold, q, p1, p2)
```

マンifold `M` の2点 `p1` と `p2` の中間を計算します。デフォルトでは [`log`](@ref) を使用し、ベクトルを2で割り、[`exp!`](@ref) を使用します。結果は `q` に保存されます。
