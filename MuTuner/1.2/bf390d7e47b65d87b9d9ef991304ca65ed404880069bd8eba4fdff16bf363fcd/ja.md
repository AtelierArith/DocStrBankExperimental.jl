```
update_forgetful_mv(x::AbstractVector{T}, V̄ₜ::T, x̄ₜ::T, c::E) where {T<:Number, E<:AbstractFloat}
```

以前の忘却分散 `V̄ₜ` と忘却平均 `x̄ₜ` の値を考慮して、更新された値 `V̄ₜ₊₁` と `x̄ₜ₊₁` を計算します。ここで、`x[end] = xₜ₊₁` はすでに `x` に追加されていると仮定します。忘却平均と分散を計算する際には、最も古い `c` 割合の値が破棄されます。
