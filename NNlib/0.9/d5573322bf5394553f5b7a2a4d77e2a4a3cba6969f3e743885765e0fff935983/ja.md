```
∇upsample_trilinear(Δ::AbstractArray{T,5}; size::NTuple{3,Integer}, align_corners::Bool = true) where T
```

# 引数

  * `Δ`: 下流層から逆伝播された入力勾配配列
  * `size`: 最初にアップサンプリングされた画像の横サイズと深さ (W,H,D)

# 出力

  * `dx`: `Δ` のダウンサンプリング版
