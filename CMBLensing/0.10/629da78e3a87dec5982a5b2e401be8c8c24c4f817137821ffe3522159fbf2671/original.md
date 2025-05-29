Returns αmax such that 𝕀 + ∇∇(ϕ + α * η) has non-zero discriminant (pixel-by-pixel) for all α values in [0, αmax]. 

This mean ϕ + αmax * η is the maximum step in the η direction which can be added to ϕ and still yield a lensing potential in the weak-lensing regime. This is important because it guarantees the potential can be paseed to LenseFlow, which cannot handle the strong-lensing / "shell-crossing" regime.
