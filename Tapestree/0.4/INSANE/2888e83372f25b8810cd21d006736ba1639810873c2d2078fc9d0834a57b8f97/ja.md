```
iTbd
```

スーパタイプ `iT` の合成再帰型で、`λ` と `μ` がジオメトリックブラウン運動として進化する二項系統樹を表し、`insane` 用に使用される、以下のフィールドを持ちます：

d1:   娘木 1   d2:   娘木 2   e:    ペンダントエッジ   iμ:   絶滅したノードの場合   fx:   固定（観測された）ノードの場合   dt:   時間遅延の選択   fdt:  最終 `dt`   lλ:   `log(λ)` のブラウン運動進化の配列   lμ:   `log(μ)` のブラウン運動進化の配列

iTbd(d1 ::iTbd,           d2 ::iTbd,           e  ::Float64,           dt ::Float64,           fdt::Float64,           iμ ::Bool,           fx ::Bool,           lλ ::Array{Float64,1},           lμ ::Array{Float64,1})
