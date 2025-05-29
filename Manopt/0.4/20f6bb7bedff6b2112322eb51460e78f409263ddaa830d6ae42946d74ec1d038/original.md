```
StochasticGradient <: AbstractGradientGroupProcessor
```

The default gradient processor, which just evaluates the (stochastic) gradient or a subset thereof.

# Constructor

```
StochasticGradient(M::AbstractManifold; p=rand(M), X=zero_vector(M, p))
```

Initialize the stochastic Gradient processor with tangent vector type of `X`, where both `M` and `p` are just help variables.
