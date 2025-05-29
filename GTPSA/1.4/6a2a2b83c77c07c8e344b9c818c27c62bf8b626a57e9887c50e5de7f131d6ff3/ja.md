```
evaluate!(y, m, x) -> y
```

`m`の`TPS`関数を点`x`で評価し、結果を含むように`y`を変更します。

# 引数

  * `y::Union{Ref{T},AbstractArray{T}}`          – `m`を`x`で評価した結果を格納するコンテナ
  * `m::Union{TPS{T,D},AbstractArray{TPS{T,D}}}` – 評価する`TPS`または`TPS`マップ
  * `x::Union{Ref{T},AbstractArray{T}}`          – `m`を評価する変数の値
