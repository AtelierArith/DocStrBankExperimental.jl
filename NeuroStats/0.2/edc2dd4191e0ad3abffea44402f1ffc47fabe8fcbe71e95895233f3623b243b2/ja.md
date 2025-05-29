```
msci95(s; <キーワード引数>)
```

平均、標準偏差、および95%信頼区間を計算します。

# 引数

  * `s::AbstractMatrix`
  * `n::Int64=3`: ブートストラップの数
  * `method::Symbol=:normal`: 正規法（`:normal`）またはn回のブートストラッピング（`:boot`）を使用

# 戻り値

名前付きタプルを含む:

  * `sm::Vector{Float64}`: 平均
  * `ss::Vector{Float64}`: 標準偏差
  * `su::Vector{Float64}`: 上側95% CI
  * `sl::Vector{Float64}`: 下側95% CI

```
