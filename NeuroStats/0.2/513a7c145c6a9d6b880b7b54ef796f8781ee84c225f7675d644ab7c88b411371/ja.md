```
efs(x1, x2)
```

効果量を計算します。

# 引数

  * `x1::AbstractVector`
  * `x2::AbstractVector`

# 戻り値

名前付きタプルを含みます：

  * `d::Float64`: コーエンのd
  * `g::Float64`: ヘッジズのg、ヘッジズとオルキンによる最尤推定量を使用
  * `Δ::Float64`: グラスのΔ
