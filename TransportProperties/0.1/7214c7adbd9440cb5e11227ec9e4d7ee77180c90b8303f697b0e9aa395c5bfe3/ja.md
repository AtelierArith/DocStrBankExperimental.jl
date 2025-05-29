自己拡散係数を計算する関数

# 使用法

```
D_ii!(D::Array{Float64},sp_trd::Array{TransportData}, T::Float64, p::Float64, molwt::Array{Float64})
```

  * D : 拡散係数を格納する配列（サイズ N）
  * sp_trd : 種の輸送データの配列
  * T : 温度（K）
  * p : 圧力（Pa）
  * molwt : 種の分子量
