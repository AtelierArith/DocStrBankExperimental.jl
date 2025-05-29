```
braid(f₁::FusionTree{I}, f₂::FusionTree{I},
        levels1::IndexTuple, levels2::IndexTuple,
        p1::IndexTuple{N₁}, p2::IndexTuple{N₂}) where {I<:Sector, N₁, N₂}
-> <:AbstractDict{Tuple{FusionTree{I, N₁}, FusionTree{I, N₂}}, <:Number}
```

入力は、分割木 `f₁` と融合木 `f₂` を使用して表現された、到着する非結合セクターのセットを出発する非結合セクターのセットに融合することを説明する融合-分割木ペアです。到着するセクター `f₂.uncoupled` は `f₁.coupled == f₂.coupled` に融合され、その後出発するセクター `f₁.uncoupled` に融合されます。新しい木と、セクター `p1` が出発し、セクター `p2` が到着するように木を再分配し、ブレーディングすることによって得られる対応する係数を計算します。分割木 `f₁` と融合木 `f₂` の非結合インデックスは、それぞれ `levels1` と `levels2` のレベル（または深さ）を持ち、インデックスがどのようにブレードするかを決定します。特に、`i` と `j` が交差する場合、$τ_{i,j}$ は `levels[i] < levels[j]` の場合に適用され、$τ_{j,i}^{-1}$ は `levels[i] > levels[j]` の場合に適用されます。これは最も一般的なブレードをエンコードすることを許可しませんが、そのような操作を組み合わせることによって一般的なブレードを得ることができます。
