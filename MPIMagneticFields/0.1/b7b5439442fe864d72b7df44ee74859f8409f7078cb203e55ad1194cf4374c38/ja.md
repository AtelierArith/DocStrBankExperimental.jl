```julia
struct LimitedSequencedField{SFT<:MPIMagneticFields.AbstractSequencedField, T<:Number} <: MPIMagneticFields.AbstractSequencedField
```

制限されたシーケンステーブルのコンテナ。

シーケンステーブルにフィールド制限を適用します。
