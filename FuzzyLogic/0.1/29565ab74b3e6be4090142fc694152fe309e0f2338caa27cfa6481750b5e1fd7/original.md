```julia
struct GaussianMF{T<:Real} <: FuzzyLogic.AbstractMembershipFunction
```

Gaussian membership function $e^{-\frac{(x-μ)²}{2σ²}}$.

### Fields

  * `mu::Real`: mean $μ$.
  * `sig::Real`: standard deviation $σ$.

### Example

```julia
mf = GaussianMF(5.0, 1.5)
```
