```
iTct
```

スーパタイプ `iT` の合成再帰型で、`λ` が幾何ブラウン運動として進化し、定数 `μ` が `insane` 用に使用される二項系統樹を表し、以下のフィールドを持ちます：

d1:   娘の木 1   d2:   娘の木 2   e:    エッジ   iμ:   絶滅したノードの場合   fx:   固定（観測された）ノードの場合   dt:   時間遅延の選択   fdt:  最終 `dt`   lλ:   `log(λ)` のブラウン運動進化の配列

iTct(d1 ::iTct,           d2 ::iTct,           e  ::Float64,           dt ::Float64,           fdt::Float64,           iμ ::Bool,           fx ::Bool,           lλ ::Array{Float64,1})
