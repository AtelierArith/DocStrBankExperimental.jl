```
SpectralGradientModel(nlp; σ = 1.0)
```

Construct a `SpectralGradientModel` rhat approximates the Hessian as `σI` from another type of nlp. The keyword argument `σ` is the initial positive multiple of the identity. See the [`SpectralGradient operator documentation`](https://juliasmoothoptimizers.github.io/LinearOperators.jl/stable/reference/#LinearOperators.SpectralGradient) for more information about the used algorithms.
