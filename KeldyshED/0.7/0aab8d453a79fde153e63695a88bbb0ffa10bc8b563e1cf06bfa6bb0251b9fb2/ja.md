```julia
toeigenbasis(
    M::Array{Array{T<:Number, 2}, 1},
    ed::KeldyshED.EDCore
) -> Vector

```

フォック状態基底で書かれたブロック対角行列を固有基底に変換します。

## 引数

  * `M`: 行列の対角ブロックのリスト。
  * `ed`: 不変部分空間構造と部分固有基底を定義する厳密対角化オブジェクト。
