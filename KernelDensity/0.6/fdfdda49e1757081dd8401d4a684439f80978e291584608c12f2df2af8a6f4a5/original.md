```julia
mutable struct UnivariateKDE{R<:AbstractRange} <: KernelDensity.AbstractKDE
```

Store both grid and density for KDE over $ℝ²$.

Reading the fields directly is part of the API, and

```julia
sum(density) * step(x) ≈ 1
```

# Fields

  * `x`: Gridpoints for evaluating the density.
  * `density`: Kernel density at corresponding gridpoints `x`.
