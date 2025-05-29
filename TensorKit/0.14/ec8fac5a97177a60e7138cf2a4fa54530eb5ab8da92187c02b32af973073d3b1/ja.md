```
repartition(f₁::FusionTree{I, N₁}, f₂::FusionTree{I, N₂}, N::Int) where {I, N₁, N₂}
-> <:AbstractDict{Tuple{FusionTree{I, N}, FusionTree{I, N₁+N₂-N}}, <:Number}
```

入力は、到着する非結合セクターのセットを出発する非結合セクターのセットに融合することを説明する二重融合木であり、出発セクター（`f₁`）と到着セクター（`f₂`）の個々の木を使用して表されます（結合されたセクターが同一であることを示す `f₁.coupled == f₂.coupled`）。`N` の出発セクターを持つために、到着セクターを出発セクターに（またはその逆に）曲げることによって木を再分配することから得られる新しい木と対応する係数を計算します。
