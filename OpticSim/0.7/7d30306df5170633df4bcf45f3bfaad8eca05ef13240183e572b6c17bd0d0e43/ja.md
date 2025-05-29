```
TriangularPrism(side_length::T, visheight::T = 2.0; interface::NullOrFresnel{T} = nullinterface(T)) -> CSGGenerator{T}
```

軸 `(0, 0, 1)` を持つ無限に高い三角柱を作成します。視覚化のために `visheight` が使用されますが、**これは表面を完全には表していないことに注意してください**。
