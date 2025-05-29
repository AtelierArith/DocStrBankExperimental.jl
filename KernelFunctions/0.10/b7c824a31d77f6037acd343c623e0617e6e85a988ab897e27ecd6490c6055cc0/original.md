```
spectral_mixture_product_kernel(
    h::Kernel=SqExponentialKernel(),
    αs::AbstractMatrix{<:Real},
    γs::AbstractMatrix{<:Real},
    ωs::AbstractMatrix{<:Real},
)
```

where αs are the weights of dimension (D, A), γs is the covariance matrix of dimension (D, A) and ωs are the mean vectors and is of dimension (D, A). Here, D is input dimension and A is the number of spectral components.

Spectral Mixture Product Kernel. With enough components A, the SMP kernel can model any product kernel to arbitrary precision, and is flexible even with a small number of components [1]

`h` is the kernel, which defaults to [`SqExponentialKernel`](@ref) if not specified.

$$
   κ(x, y) = Πᵢ₌₁ᴷ Σ(αsᵢᵀ .* (h(-(γsᵢᵀ * tᵢ)²) .* cos(ωsᵢᵀ * tᵢ))), tᵢ = xᵢ - yᵢ
$$

# References:

```
[1] GPatt: Fast Multidimensional Pattern Extrapolation with GPs,
    arXiv 1310.5288, 2013, by Andrew Gordon Wilson, Elad Gilboa,
    Arye Nehorai and John P. Cunningham
```
