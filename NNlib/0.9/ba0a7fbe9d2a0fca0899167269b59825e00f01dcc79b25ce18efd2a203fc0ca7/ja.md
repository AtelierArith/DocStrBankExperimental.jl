```
∇upsample_bilinear(Δ::AbstractArray{T,4}; size::NTuple{2,Integer}, align_corners::Bool = true) where T
```

# 引数

  * `Δ`: 下流層から逆伝播された入力勾配配列
  * `size`: 最初にアップサンプリングされた画像の横（W,H）サイズ

# 出力

  * `dx`: `Δ`のダウンサンプリングされたバージョン
