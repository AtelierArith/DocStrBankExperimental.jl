```
∇upsample_linear(Δ::AbstractArray{T,3}; size::Integer, align_corners::Bool = true) where T
```

# 引数

  * `Δ`: 下流レイヤーから逆伝播された入力勾配配列
  * `size`: 最初にアップサンプリングされた画像のサイズ

# 出力

  * `dx`: `Δ`のダウンサンプリングされたバージョン
