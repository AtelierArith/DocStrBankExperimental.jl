```
ℝⁿ2ℂⁿ_function(f::Function, p::AbstractArray{T})
```

Helper function for performing uncertainty propagation through complex-valued functions with vector inputs. Applies  `f : ℝⁿ → Cⁿ` to an array of particles. E.g., `LinearAlgebra.eigvals(p::Matrix{<:AbstractParticles}) = ℝⁿ2ℂⁿ_function(eigvals,p)`
