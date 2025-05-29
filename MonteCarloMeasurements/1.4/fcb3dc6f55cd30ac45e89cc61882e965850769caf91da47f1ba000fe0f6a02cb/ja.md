```
ℝⁿ2ℂⁿ_function(f::Function, p::AbstractArray{T})
```

複素値関数に対する不確実性伝播をベクトル入力で行うためのヘルパー関数。`f : ℝⁿ → Cⁿ` を粒子の配列に適用します。例えば、`LinearAlgebra.eigvals(p::Matrix{<:AbstractParticles}) = ℝⁿ2ℂⁿ_function(eigvals,p)`
