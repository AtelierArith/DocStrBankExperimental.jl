```
add_joint!(g::BVHGraph, v₋₁::Integer, name::AbstractString, off::Vector{Float64}, nb::Vector = outneighbors(g, v₋₁))
```

`v₋₁`のアウトネイバーとして、オフセット`off`を持つ名前`name`の頂点を追加します。新しい頂点に接続されるべき`v₋₁`のアウトネイバーは指定できます。

"JOINT"は自動的に`name`の前に追加されます。`v₋₁`はその名前でも識別できます。
