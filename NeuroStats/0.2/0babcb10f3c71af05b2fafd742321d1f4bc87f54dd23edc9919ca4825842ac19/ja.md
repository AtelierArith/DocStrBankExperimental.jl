```
msci95(s; <キーワード引数>)
```

平均、標準偏差、および95%信頼区間を計算します。

# 引数

  * `s::AbstractVector`
  * `n::Int64=3`: ブートストラップの数
  * `method::Symbol=:normal`: 正規法（`:normal`）またはn回のブートストラッピング（`:boot`）を使用

# 戻り値

名前付きタプルを含む:

  * `sm::Float64`: 平均
  * `ss::Float64`: 標準偏差
  * `su::Float64`: 上側95% CI
  * `sl::Float64`: 下側95% CI

```
