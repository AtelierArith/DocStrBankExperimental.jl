```
batched_jacobian(f, backend::AbstractADType, x::AbstractArray)
```

Computes the Jacobian of a function `f` with respect to a batch of inputs `x`. This expects the following properties for `y = f(x)`:

1. `ndims(y) ≥ 2`
2. `size(y, ndims(y)) == size(x, ndims(x))`

## Backends & AD Packages

| Supported Backends | Packages Needed |
|:------------------ |:--------------- |
| `AutoForwardDiff`  |                 |
| `AutoZygote`       | `Zygote.jl`     |

## Arguments

  * `f`: The function to compute the jacobian of.
  * `backend`: The backend to use for computing the jacobian.
  * `x`: The input to the function. Must have `ndims(x) ≥ 2`.

## Returns

  * `J`: The Jacobian of `f` with respect to `x`. This will be a 3D Array. If the dimensions of `x` are `(N₁, N₂, ..., Nₙ, B)` and of `y` are `(M₁, M₂, ..., Mₘ, B)`, then `J` will be a `((M₁ × M₂ × ... × Mₘ), (N₁ × N₂ × ... × Nₙ), B)` Array.

!!! danger
    `f(x)` must not be inter-mixing the batch dimensions, else the result will be incorrect. For example, if `f` contains operations like batch normalization, then the result will be incorrect.

