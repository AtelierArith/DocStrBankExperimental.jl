```
stdp(s1, s2, n1, n2; <keyword arguments>)
```

異なるグループの被験者数のときにプールされた標準偏差を計算します。

# 引数

  * `s1::Real`
  * `s2::Real`
  * `n1::Int64`
  * `n2::Int64`
  * `type::Symbol=:cohen`: コーエンの方程式（`:cohen`）またはヘッジズとオルキンによる最尤推定量（`:hedges`）を使用

# 戻り値

  * `ps::Float64`
