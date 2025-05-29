```
permute(f₁::FusionTree{I}, f₂::FusionTree{I},
        p1::NTuple{N₁, Int}, p2::NTuple{N₂, Int}) where {I, N₁, N₂}
-> <:AbstractDict{Tuple{FusionTree{I, N₁}, FusionTree{I, N₂}}, <:Number}
```

入力は、到着する未結合セクターのセットを出発する未結合セクターのセットに融合することを説明する二重融合木であり、出発セクター（`t1`）と到着セクター（`t2`）の個々の木を使用して表されます（結合されたセクター `t1.coupled == t2.coupled` が同一であること）。新しい木と、セクター `p1` が出発し、セクター `p2` が到着するように木を再配分および順列することによって得られる対応する係数を計算します。
