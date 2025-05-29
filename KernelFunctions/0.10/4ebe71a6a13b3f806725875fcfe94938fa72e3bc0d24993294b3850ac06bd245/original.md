```
spectral_mixture_kernel(
    h::Kernel=SqExponentialKernel(),
    αs::AbstractVector{<:Real},
    γs::AbstractMatrix{<:Real},
    ωs::AbstractMatrix{<:Real},
)
```

where αs are the weights of dimension (A, ), γs is the covariance matrix of dimension (D, A) and ωs are the mean vectors and is of dimension (D, A). Here, D is input dimension and A is the number of spectral components.

`h` is the kernel, which defaults to [`SqExponentialKernel`](@ref) if not specified.

!!! warning
    If you want to make sure that the constructor is type-stable, you should provide [`StaticArrays`](https://github.com/JuliaArrays/StaticArrays.jl) arguments: `αs` as a `StaticVector`, `γs` and `ωs` as `StaticMatrix`.


Generalised Spectral Mixture kernel function. This family of functions is  dense in the family of stationary real-valued kernels with respect to the pointwise convergence.[1]

$$
   κ(x, y) = αs' (h(-(γs' * t)^2) .* cos(π * ωs' * t), t = x - y
$$

# References:

```
[1] Generalized Spectral Kernels, by Yves-Laurent Kom Samo and Stephen J. Roberts
[2] SM: Gaussian Process Kernels for Pattern Discovery and Extrapolation,
        ICML, 2013, by Andrew Gordon Wilson and Ryan Prescott Adams,
[3] Covariance kernels for fast automatic pattern discovery and extrapolation
    with Gaussian processes, Andrew Gordon Wilson, PhD Thesis, January 2014.
    http://www.cs.cmu.edu/~andrewgw/andrewgwthesis.pdf
[4] http://www.cs.cmu.edu/~andrewgw/pattern/.
```
