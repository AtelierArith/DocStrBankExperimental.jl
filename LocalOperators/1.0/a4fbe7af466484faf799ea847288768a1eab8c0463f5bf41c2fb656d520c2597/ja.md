```
LocalOperator{T<:Number} <: AbstractMatrix{T}
```

テンソル積のローカルベクトル空間に作用する行列演算子に対応する具体的な型です。この演算子は、フィールド `data` に格納された行列として、フィールド `support` によって定義されたローカルベクトル空間上で作用し、それ以外の場所では単位行列として作用します。

# フィールド

  * `data::Matrix{T}`: 演算子の行列表現を格納します
  * `support::UnitRange{Int}`: 演算子がサポートを持つサイトを格納します
