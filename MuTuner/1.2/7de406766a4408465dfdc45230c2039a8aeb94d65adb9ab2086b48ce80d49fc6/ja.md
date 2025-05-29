```
update_forgetful_mean(x::AbstractVector{T}, x̄ₜ::T, c::E) where {T<:Number, E<:AbstractFloat}
```

以前の忘却平均の値 `x̄ₜ` を考慮して、`x` に `x[end] = xₜ₊₁` が既に追加されていると仮定した場合、その更新された値 `x̄ₜ₊₁` を計算します。忘却平均を計算する際には、最も古い `c` 割合の値が破棄されます。
