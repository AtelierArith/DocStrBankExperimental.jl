二量子ビットゲートのワイル空間座標 c₁, c₂, c₃ を計算します。

```julia
c₁, c₂, c₃ = weyl_chamber_coordinates(U)
```

これは、[ChildsPRA2003](@citet) に記載されたアルゴリズムを使用してワイル空間座標を計算します。

# 参考文献

  * [ChildsPRA2003](@cite) Childs *et al.*. Phys. Rev. A 68, 052311 (2003)
