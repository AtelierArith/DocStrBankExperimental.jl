最大ゲート共役を計算します。

```julia
C = gate_concurrence(U)
C = gate_concurrence(c₁, c₂, c₃)
```

これは、2つの2量子ビットゲート `U`、およびウェイユチャンバー座標 `c₁`、`c₂`、`c₃`（参照：[`weyl_chamber_coordinates`](@ref)）によって生成される最大共役 $C ∈ [0, 1]$ を計算します。

# 参考文献

  * [KrausPRA2001](@cite) Kraus and Cirac, Phys. Rev. A 63, 062309 (2001)
