```
root_union!(s::IntDisjointSets{T}, x::T, y::T)
```

x と y の根要素を持つ二つの集合の和集合を形成し、新しい集合の根を返します。x ≠ y と仮定します（安全ではありません）。
