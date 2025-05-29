```
RegularizationProblem
```

This data type contains the cached matrices used in the inversion. The problem is  initialized using the constructor [setupRegularizationProblem](@ref) with the design matrix  A and the the Tikhonv matrix L as inputs. The hat quantities, e.g. Ā, is the calculated design matrix in standard form. ĀĀ, Āᵀ, F̄ are precomputed to speed up repeating inversions with different data. L⁺ₐ is cached to speed up the repeated conversion of  data [to_standard_form](@ref) and [to_general_form](@ref)

```
Ā::Matrix{Float64}     # Standard form of design matrix
A::Matrix{Float64}     # General form of the design matrix (n×p)
L::Matrix{Float64}     # Smoothing matrix (n×p)
ĀĀ::Matrix{Float64}    # Cached value of Ā'Ā for performance
Āᵀ::Matrix{Float64}    # Cached value of Ā' for performance
F̄::SVD                 # Cached SVD decomposition of Ā 
Iₙ::Matrix{Float64}    # Cached identity matrix n×n
Iₚ::Matrix{Float64}    # Cached identity matrix p×p
K₀T⁻¹H₀ᵀ::Matrix{Float64} # Cached value to compute 2.42 and 2.44 in Hansen ch 2.
```
