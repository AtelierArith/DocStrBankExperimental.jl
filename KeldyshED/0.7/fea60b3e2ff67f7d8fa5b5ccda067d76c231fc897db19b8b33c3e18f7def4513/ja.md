```julia
tofockbasis(
    M::Array{Array{T<:Number, 2}, 1},
    ed::KeldyshED.EDCore
) -> Vector

```

固有基で書かれたブロック対角行列をフォック状態基底に変換します。

## 引数

  * `M`: 行列の対角ブロックのリスト。
  * `ed`: 不変部分空間構造と部分固有基を定義する厳密対角化オブジェクト。
