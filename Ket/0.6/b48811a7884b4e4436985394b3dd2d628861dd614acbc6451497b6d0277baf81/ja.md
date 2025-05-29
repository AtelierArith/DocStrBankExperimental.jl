```
choi(K::Vector{<:AbstractMatrix})
```

Kraus演算子`K`によって与えられるCP写像のChoi-Jamiołkowski表現を構築します。使用される規約は、choi(K) = ∑ᵢⱼ |i⟩⟨j|⊗K|i⟩⟨j|K'です。
