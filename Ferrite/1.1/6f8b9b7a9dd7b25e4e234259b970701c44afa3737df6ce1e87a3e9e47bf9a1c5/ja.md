```
PointLocation
```

[`PointIterator`](@ref) の要素で、通常は [`PointValues`](@ref) を再初期化するために使用されます。フィールド：

  * `cid::Int`: 点を含むセルのID
  * `local_coord::Vec`: 点のローカル（参照）座標
  * `coords::Vector{Vec}`: セルの座標
