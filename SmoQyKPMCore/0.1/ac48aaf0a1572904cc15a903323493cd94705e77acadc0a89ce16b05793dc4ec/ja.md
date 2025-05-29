```
kpm_mul(A, kpm_expansion::KPMExpansion, v::T) where {T<:AbstractVecOrMat}
```

ベクトル $v^\prime = F(A) \cdot v$ を評価して返します。ここで、$F(A)$ はチェビシェフ展開によって表されます。詳細については [`kpm_mul!`](@ref) を参照してください。
