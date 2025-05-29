```
kpm_mul(
    A, coefs::AbstractVector, bounds, v::T, tmp = zeros(eltype(v), size(v)..., 3)
) where {T<:AbstractVecOrMat}
```

ベクトル $v^\prime = F(A) \cdot v$ を評価して返します。ここで、$F(A)$ はチェビシェフ展開によって表されます。詳細については [`kpm_mul!`](@ref) を参照してください。
