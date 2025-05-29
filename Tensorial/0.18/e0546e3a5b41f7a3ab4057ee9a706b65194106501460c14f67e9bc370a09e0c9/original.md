```
deviatoric_stress_invariants(::AbstractSecondOrderTensor{3})
deviatoric_stress_invariants(::AbstractSymmetricSecondOrderTensor{3})
deviatoric_stress_invariants(::Vec{3})
```

Return a tuple storing deviatoric stress invariants.

$$
\begin{aligned}
J_1(\bm{\sigma}) &= \mathrm{tr}(\mathrm{dev}(\bm{\sigma})) = 0 \\
J_2(\bm{\sigma}) &= \frac{1}{2} \mathrm{tr}(\mathrm{dev}(\bm{\sigma})^2) \\
J_3(\bm{\sigma}) &= \frac{1}{3} \mathrm{tr}(\mathrm{dev}(\bm{\sigma})^3)
\end{aligned}
$$

# Examples

```jldoctest
julia> σ = rand(SymmetricSecondOrderTensor{3})
3×3 SymmetricSecondOrderTensor{3, Float64, 6}:
 0.325977  0.549051  0.218587
 0.549051  0.894245  0.353112
 0.218587  0.353112  0.394255

julia> J₁, J₂, J₃ = deviatoric_stress_invariants(σ)
(0.0, 0.5701886673667987, 0.14845380911930367)
```
