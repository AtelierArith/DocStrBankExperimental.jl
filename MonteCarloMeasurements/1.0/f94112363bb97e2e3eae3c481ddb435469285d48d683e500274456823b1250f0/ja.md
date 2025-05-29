```
ℝⁿ2ℝⁿ_function(f::Function, p::AbstractArray{T})
```

ベクトル入力を持つベクトル値関数を通じて不確実性伝播を行うためのヘルパー関数。配列の粒子に `f : ℝⁿ → ℝⁿ` を適用します。例えば、`Base.log(p::Matrix{<:AbstractParticles}) = ℝⁿ2ℝⁿ_function(log,p)`
