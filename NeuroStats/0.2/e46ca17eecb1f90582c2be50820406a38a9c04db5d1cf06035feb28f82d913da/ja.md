```
stdp(x1, x2; <キーワード引数>)
```

プールされた標準偏差を計算します。

# 引数

  * `x1::AbstractVector`
  * `x2::AbstractVector`
  * `type::Symbol=:cohen`: コーエンの方程式（`:cohen`）またはヘッジズとオルキンによる最尤推定量（`:hedges`）を使用

# 戻り値

  * `ps::Float64`
