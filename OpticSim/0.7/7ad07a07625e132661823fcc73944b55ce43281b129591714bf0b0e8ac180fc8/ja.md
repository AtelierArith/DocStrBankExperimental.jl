```
HexagonalPrism(side_length::T, visheight::T = 2.0; interface::NullOrFresnel{T} = nullinterface(T)) -> CSGGenerator{T}
```

高さが無限の六角柱を作成します。軸は `(0, 0, 1)` で、長い六角形の直径は x 軸に沿っています。視覚化のために `visheight` が使用されますが、**これは表面を完全には表していないことに注意してください**。
