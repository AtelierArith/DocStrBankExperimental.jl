```julia
struct SequencedField{FT<:MPIMagneticFields.AbstractMagneticField, ST<:MPIMagneticFields.Sequence} <: MPIMagneticFields.AbstractSequencedField
```

シーケンスフィールドのコンテナ。

時間にわたる動きを定義するフィールドにシーケンスを添付します。
