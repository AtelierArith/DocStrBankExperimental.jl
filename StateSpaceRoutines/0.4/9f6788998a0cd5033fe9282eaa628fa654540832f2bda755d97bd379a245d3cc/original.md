```
correction!(inc_weights, norm_weights, φ_new, coeff_terms, log_e_1_terms,
     log_e_2_terms, n_obs)
```

Compute (and modify in-place) incremental weights w̃ₜʲ and normalized weights W̃ₜʲ:

```
    w̃ₜʲ(φₙ) = pₙ(yₜ|sₜʲ'ⁿ⁻¹) / pₙ₋₁(yₜ|sₜʲ'ⁿ⁻¹)
            = (φₙ/φₙ₋₁)^(d/2) exp{-1/2 (φₙ-φₙ₋₁) [yₜ-Ψ(sₜʲ'ⁿ⁻¹)]' Σᵤ⁻¹ [yₜ-Ψ(sₜʲ'ⁿ⁻¹)]}

    W̃ₜʲ(φₙ) = w̃ₜʲ(φₙ) / (1/M) ∑ w̃ₜʲ(φₙ)
```
