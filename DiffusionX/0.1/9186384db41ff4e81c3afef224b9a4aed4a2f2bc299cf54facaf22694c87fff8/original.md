````
``\alpha``-Stable distribution.

# Parameters
- `α`: Stability parameter.
- `β`: Skewness parameter.
- `σ`: Scale parameter.
- `μ`: Location parameter.

# Examples
```julia
using DiffusionX
S = Stable(1.0, 0.0, 1.0, 0.0)
rand(S)
```
````
