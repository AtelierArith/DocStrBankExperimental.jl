与えられたゲートが（特定の領域の）ワイル室にあるかどうかを確認します。

```
in_weyl_chamber(c₁, c₂, c₃)
```

は、`c₁`、`c₂`、`c₃`が有効なワイル室座標であるかどうかを確認します。

```
in_weyl_chamber(U; region="PE")
in_weyl_chamber(c₁, c₂, c₃; region="PE")
```

は、2量子ビットゲート`U`、およびワイル室座標`c₁`、`c₂`、`c₃`（[`weyl_chamber_coordinates`](@ref)を参照）で説明されるゲートが完璧なエンタングラーであるかどうかを確認します。`region`は、[`weyl_chamber_region`](@ref)によって返される他の領域のいずれかにすることができます。
