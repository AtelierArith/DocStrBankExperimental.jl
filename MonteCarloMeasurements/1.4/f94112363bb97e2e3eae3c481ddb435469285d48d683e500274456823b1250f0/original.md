```
ℝⁿ2ℝⁿ_function(f::Function, p::AbstractArray{T})
```

Helper function for performing uncertainty propagation through vector-valued functions with vector inputs. Applies  `f : ℝⁿ → ℝⁿ` to an array of particles. E.g., `Base.log(p::Matrix{<:AbstractParticles}) = ℝⁿ2ℝⁿ_function(log,p)`
