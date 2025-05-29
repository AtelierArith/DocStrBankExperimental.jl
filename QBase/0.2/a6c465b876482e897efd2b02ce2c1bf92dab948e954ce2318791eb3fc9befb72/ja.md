```
generalized_bell_states( dim :: Int64 ) :: Vector{State{ComplexF64}
```

一般化ベル基底の密度行列。詳細については [`generalized_bell_kets`](@ref) を参照してください。`dim ≥ 2` が満たされない場合、`DomainError` がスローされます。
