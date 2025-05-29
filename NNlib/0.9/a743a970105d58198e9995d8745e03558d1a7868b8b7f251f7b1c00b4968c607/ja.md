```
∇upsample_nearest(Δ::AbstractArray{T,3}, scales::NTuple{S, <:Integer}) where T
```

# 引数

  * `Δ`: 下流層から逆伝播された入力勾配配列
  * `scales`: 画像が最初にアップサンプリングされたスケール

# 出力

  * `dx`: `Δ`のダウンサンプリングされたバージョン
