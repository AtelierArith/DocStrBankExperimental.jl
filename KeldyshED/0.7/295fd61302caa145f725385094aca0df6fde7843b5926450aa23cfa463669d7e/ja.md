```julia
full_hs_matrix(
    M::Array{Array{T<:Number, 2}, 1},
    ed::KeldyshED.EDCore
) -> Matrix{T} where T<:Number

```

ブロック対角行列をフラットにし、全ヒルベルト空間で作用する行列を返します。

## 引数

  * `M`: 行列の対角ブロックのリスト。
  * `ed`: 不変部分空間構造を定義する厳密対角化オブジェクト。
