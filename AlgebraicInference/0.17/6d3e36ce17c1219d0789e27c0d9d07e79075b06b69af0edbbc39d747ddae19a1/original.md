```
GaussianSystem(
    P::AbstractMatrix,
    S::AbstractMatrix,
    p::AbstractVector,
    s::AbstractVector,
    σ::Real)
```

Construct a Gaussian system by specifying its energy function. You should set

```julia
σ  = dot(s, pinv(S) * s)
```
