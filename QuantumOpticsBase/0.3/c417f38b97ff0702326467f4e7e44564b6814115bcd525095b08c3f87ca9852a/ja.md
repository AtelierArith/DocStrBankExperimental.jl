```
tensor(a::AbstractOperator, b::Bra)
tensor(a::Bra, b::AbstractOperator)
tensor(a::AbstractOperator, b::Ket)
tensor(a::Ket, b::AbstractOperator)
```

演算子と状態ベクトルの積 $a ⊗ <b|$。演算子がユニタリで状態が正規化されている場合、結果は等長写像です。
