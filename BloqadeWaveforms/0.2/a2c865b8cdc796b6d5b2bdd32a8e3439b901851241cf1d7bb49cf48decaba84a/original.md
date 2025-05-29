```
smooth(kernel, Xi::Vector, Yi::Vector, kernel_radius::Real)
```

Kernel smoother function via weighted moving average method. See also [Kernel Smoother](https://en.wikipedia.org/wiki/Kernel_smoother).

# Theory

Kernel function smoothing is a technique to define a smooth function $f: \mathcal{R}^p → \mathbf{R}$ from a set of discrete points by weighted averaging the neighboring points. It can be written as the following equation.

$$
Ŷ(X) = \sum_i K(X, X_i) Y_i / \sum_i K(X, X_i)
$$

where $Ŷ(X)$ is the smooth function by calculating the moving average of known data points $X_i$ and $Y_i$. `K` is the kernel function, where $K(\frac{||X - X_i||}{h_λ})$ decrease when the Euclidean norm $||X - X_i||$ increase, $h_λ$ is a parameter controls the radius of the kernel.

# Available Kernels

The following kernel functions are available via the [`Kernels`](@ref) module:

[`Kernels.biweight`](@ref); [`Kernels.cosine`](@ref); [`Kernels.gaussian`](@ref); [`Kernels.logistic`](@ref); [`Kernels.parabolic`](@ref); [`Kernels.sigmoid`](@ref); [`Kernels.triangle`](@ref); [`Kernels.tricube`](@ref); [`Kernels.triweight`](@ref); [`Kernels.uniform`](@ref)

# Arguments

  * `kernel`: a Julia function that has method `kernel(t::Real)`.
  * `Xi::Vector`: a list of inputs `X_i`.
  * `Yi::Vector`: a list of outputs `Y_i`.
  * `kernel_radius::Real`: the radius of the kernel.
