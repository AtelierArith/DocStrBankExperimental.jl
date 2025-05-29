```
KernelLabel
```

Constructors:

  * `KernelLabel(x::AbstractArray, c::AbstractVector, σ::Number;`               `kernel::Symbol=:SquaredExponential)`
  * `KernelLabel(x::AbstractArray, c::AbstractVector, σ::AbstractArray;`               `kernel::Symbol=:SquaredExponential)`

An approximately invariant kernel label function.

Constructor elements:

  * `x`: The `d` × `2N` array of interpolating points, where `x[:, n+N] = F(x[:, n])` for `n<=N` and some symplectic map `F`.
  * `c`: The length `2N` vector of coefficients of the kernel function
  * `σ`: The length scale of the kernel (if a vector, length scale is different in different directions)
  * `kernel`: The type of kernel used

The current supported kernels are:

  * `:SquaredExponential`: The squared exponential kernel   K(x, y) = exp(-|x-y|²)
  * `:InverseMultiquadric`: The β=1 Inverse Multiquadric kernel   K(x, y) = (1+|x-y|²)^(-1/2)
  * `:FourierSE`: The Fourier × Cartesian squared exponential kernel   K(x, y) = exp(-sin²(x₁-y₁) - (x₂-y₂)²)
  * `:Fourier`: The Fourier × Fourier squared exponential kernel   K(x, y) = exp(-sin²(x₁-y₁) - sin²(x₂-y₂))
