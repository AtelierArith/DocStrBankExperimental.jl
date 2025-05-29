```
Model(; mesh, ρ, D, T₂, κ, γ)
```

Finite element discretized biological model with initial spin densities `ρ`, diffusion tensors `D`, T₂-relaxation times `T₂`, wall permeabilities `κ`, and gyromacnetic ratio `γ`. The vectors `ρ`, `D`, `T₂`, are of length `ncompartment`, while `κ` is of length `nboundary`.
