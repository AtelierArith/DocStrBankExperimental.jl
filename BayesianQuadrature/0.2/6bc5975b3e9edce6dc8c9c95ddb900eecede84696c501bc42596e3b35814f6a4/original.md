```
BayesQuad(k::Kernel; l=1.0, σ::Real=1.0)
```

Tool for estimating the bayesian quadrature for a given `BayesQuadModel` and a `Sampler`.

`BayesQuad` estimate the probability distribution `p(I)` of I = ∫ f(x) p(x) dx

## Argument

  * `k::Kernel` : kernel from `KernelFunctions.jl`, the kernel cannot be composite

## Keywords argument

  * `l` : lengthscale of the kernel. It can be:

      * `Real` : isotropic kernel
      * `AbstractVector` : ARD kernel (one lengthscale per dimension)
      * `LowerTriangular` : Linear transformation of the inputs
  * `σ` : variance of the kernel (`k(x,x') -> σ * k(x,x')`)

Note: If `k` already has a variance and/or a transformation, these will be automatically extracted and replace the given keyword arguments
