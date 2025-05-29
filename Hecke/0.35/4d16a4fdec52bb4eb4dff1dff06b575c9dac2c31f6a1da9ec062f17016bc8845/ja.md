```
reduced_resultant(f::PolyRingElem{T}, g::PolyRingElem{T}) where T <: ResElem{S} where S <: IntegerUnion -> T
```

$$
f
$$

と $g$ の縮小結果を二次時間アルゴリズムを使用して計算します。すなわち、$(f, g) \cap Z$ の生成元です。
