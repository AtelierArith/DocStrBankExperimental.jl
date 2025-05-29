```
SpectralKernelOperator(transform, channels, σ = identity; init = glorot_uniform)
```

Constructs a spectral kernel operator with spectral transform `trafo`, channels `channels`,  activation function `σ`, and initialization function `init`.

References: Fourier Neural Operator for Parametric Partial Differential Equations - https://arxiv.org/abs/2010.08895

# Example

```
julia> trafo = FourierTransform(modes = (12, 3, 4, 12))
julia> channels = 1 => 4
julia> σ = relu
julia> conv = SpectralKernelOperator(trafo, channels, σ)
```
