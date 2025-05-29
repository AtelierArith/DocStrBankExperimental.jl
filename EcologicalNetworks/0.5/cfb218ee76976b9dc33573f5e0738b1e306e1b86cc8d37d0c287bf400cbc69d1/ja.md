```
mpnmodel(S::Int64, Co::Float64, forbidden::Float64)
```

与えられた `S` の数、接続性 `Co` および `forbidden` リンク発生の確率に基づいて、最小潜在ニッチモデルに従ってリンクが割り当てられた `UnipartiteNetwork` を返します。

#### 参考文献

Allesina, S., Alonso, D., Pascual, M., 2008. A General Model for Food Web Structure. Science 320, 658–661. https://doi.org/10.1126/science.1156269
