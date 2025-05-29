```
comp_psd_adfriendly(x::AbstractArray{<:Real}, fs::Real; dims::Int=ndims(x))
```

自動微分（AD）に優しい実装を使用してパワースペクトル密度を計算します。

# 引数

  * `x`: 時系列データ
  * `fs`: サンプリング周波数
  * `dims=ndims(x)`: PSDを計算する次元

# 戻り値

  * `power`: パワースペクトル密度の値
  * `freqs`: 対応する周波数
