```
sTxs
```

スーパタイプ `Tx` の合成再帰型で、特性 `xv` とそのレート `lσ2` を持つ二項系統樹を表します。以下のフィールドがあります：

d1:   娘木 1   d2:   娘木 2   e:    エッジ   dt:   時間遅延の選択   fdt:  最終 `dt`   xv:   `X` のブラウン運動の進化の配列。   lσ2:  `log(σ)` のブラウン運動の進化の配列。

sTxs(d1 ::sTxs,        d2 ::sTxs,        e  ::Float64,        dt ::Float64,        fdt::Float64,        xv ::Array{Float64,1},        lσ2 ::Array{Float64,1})
