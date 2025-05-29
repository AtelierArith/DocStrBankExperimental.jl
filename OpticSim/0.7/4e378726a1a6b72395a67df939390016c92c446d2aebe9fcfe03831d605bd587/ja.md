```
RectangularPrism(halfsizex::T, halfsizey::T, visheight::T=2.0; interface::NullOrFresnel{T} = nullinterface(T)) -> CSGGenerator{T}
```

無限に高い直方体を軸 `(0, 0, 1)` で作成します。視覚化のために `visheight` が使用されますが、**これは表面を完全には表していないことに注意してください**。
