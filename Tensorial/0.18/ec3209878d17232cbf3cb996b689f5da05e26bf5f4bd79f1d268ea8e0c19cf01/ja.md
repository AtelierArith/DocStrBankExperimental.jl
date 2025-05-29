```
stress_invariants(::AbstractSecondOrderTensor{3})
stress_invariants(::AbstractSymmetricSecondOrderTensor{3})
stress_invariants(::Vec{3})
```

応力不変量を格納するタプルを返します。

$$
\begin{aligned}
I_1(\bm{\sigma}) &= \mathrm{tr}(\bm{\sigma}) \\
I_2(\bm{\sigma}) &= \frac{1}{2} (\mathrm{tr}(\bm{\sigma})^2 - \mathrm{tr}(\bm{\sigma}^2)) \\
I_3(\bm{\sigma}) &= \det(\bm{\sigma})
\end{aligned}
$$

# 例

```jldoctest
julia> σ = rand(SymmetricSecondOrderTensor{3})
3×3 SymmetricSecondOrderTensor{3, Float64, 6}:
 0.325977  0.549051  0.218587
 0.549051  0.894245  0.353112
 0.218587  0.353112  0.394255

julia> I₁, I₂, I₃ = stress_invariants(σ)
(1.6144775244804341, 0.2986572249840249, -0.0025393241133506677)
```
