```julia
mutable struct BivariateKDE{Rx<:AbstractRange, Ry<:AbstractRange} <: KernelDensity.AbstractKDE
```

Store both grid and density for KDE over the real line.

Reading the fields directly is part of the API, and

```julia
sum(density) * step(x) * step(y) ≈ 1
```

# Fields

  * `x`: First coordinate of gridpoints for evaluating the density.
  * `y`: Second coordinate of gridpoints for evaluating the density.
  * `density`: Kernel density at corresponding gridpoints `Tuple.(x, permutedims(y))`.
