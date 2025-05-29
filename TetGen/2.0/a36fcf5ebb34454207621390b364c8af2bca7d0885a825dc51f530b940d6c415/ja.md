```julia
struct RawFacet{T}
```

TetGenへの入力の一部としての複雑なファセット。

  * `polygonlist::Vector{Vector{Int32}}`: 入力点を記述するpointlist配列を指すインデックスの配列として与えられたポリゴン。
  * `holelist::Matrix`: ファセット内の穴を記述するポリゴンを示す座標によって与えられた点の配列。
