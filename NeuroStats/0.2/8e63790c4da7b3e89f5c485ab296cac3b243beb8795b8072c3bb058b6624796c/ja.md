```
msci95(s; <キーワード引数>)
```

平均、標準偏差、および95%信頼区間を計算します。

# 引数

  * `s::AbstractArray`
  * `n::Int64=3`: ブートストラップの数
  * `method::Symbol=:normal`: 正規法（`:normal`）またはn回のブートストラッピング（`:boot`）を使用

# 戻り値

名前付きタプルを含む：

  * `sm::Matrix{Float64}`: 平均
  * `ss::Matrix{Float64}`: 標準偏差
  * `su::Matrix{Float64}`: 上側95% CI
  * `sl::Matrix{Float64}`: 下側95% CI
