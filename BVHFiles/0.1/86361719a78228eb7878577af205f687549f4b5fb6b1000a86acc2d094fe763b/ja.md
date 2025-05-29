```
add_joint!(g::BVHGraph, v₋₁::Integer, v₊₁::Integer, name::AbstractString; fraction::Float64 = 0.5)
```

`v₋₁`と`v₊₁`の間の直線上に`name`という名前の頂点を追加します。`fraction`は、新しい頂点に割り当てられる古いオフセットの割合を指します。

"JOINT"は自動的に`name`の前に追加されます。`v₋₁`と`v₊₁`は名前でも識別できます。
