```
tensor_probability(rho::Hermitian, all_Aax::Vector{Measurement}...)
tensor_probability(rho::Hermitian, Aax::Vector{Measurement}, N::Integer)
```

状態 `rho` に N セットの測定を適用して確率配列を形成します。すべての当事者が同じ測定を適用する場合は、短縮表記を使用します。
