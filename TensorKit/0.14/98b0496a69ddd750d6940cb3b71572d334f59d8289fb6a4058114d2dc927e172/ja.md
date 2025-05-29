```
⊕(V₁::S, V₂::S, V₃::S...) where {S<:ElementarySpace} -> S
oplus(V₁::S, V₂::S, V₃::S...) where {S<:ElementarySpace} -> S
```

対応するベクトル空間の型 `S` を返します。これは、空間 `V₁`、`V₂`、... の直和を表します。すべての個々の空間は [`isdual`](@ref) の値が同じである必要があることに注意してください。そうでない場合、直和は定義されません。
