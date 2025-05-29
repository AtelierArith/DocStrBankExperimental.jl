```
iTfbd
```

スーパタイプ `iT` の合成再帰型で、化石を持つ `insane` 用の二項系統樹を表し、`λ` と `μ` が幾何ブラウン運動として進化します。以下のフィールドがあります：

d1:   娘木 1   d2:   娘木 2   e:    ペンダントエッジ   iμ:   絶滅ノードの場合   iψ:   化石の場合   fx:   固定（観測）ノードの場合   dt:   時間遅延の選択   fdt:  最終 `dt`   lλ:   `log(λ)` のブラウン運動進化の配列   lμ:   `log(μ)` のブラウン運動進化の配列

iTfbd(d1 ::iTfbd,         d2 ::iTfbd,         e  ::Float64,         dt ::Float64,         fdt::Float64,         iμ ::Bool,         iψ ::Bool,         fx ::Bool,         lλ ::Array{Float64,1},         lμ ::Array{Float64,1})
