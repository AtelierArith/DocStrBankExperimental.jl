```
summary(x)
```

要約統計量を返します。

# 引数

  * `x::AbstractVector`

# 戻り値

名前付きタプルを含む：

  * `mm::Float64`: 平均
  * `v::Float64`: 分散
  * `s::Float64`: 標準偏差
  * `me::Float64`: 中央値
  * `mo::Float64`: 最頻値
