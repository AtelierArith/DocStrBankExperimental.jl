```
NestedQuad(alg::IntegralAlgorithm)
NestedQuad(algs::IntegralAlgorithm...)
```

Nested integration by repeating one quadrature algorithm or composing a list of algorithms. The domain of integration must be an `AbstractIteratedLimits` from the IteratedIntegration.jl package. Analogous to `nested_quad` from IteratedIntegration.jl. The integrand should expect `SVector` inputs. Do not use this for very high-dimensional integrals, since the compilation time scales very poorly with respect to dimensionality. In order to improve the compilation time, FunctionWrappers.jl is used to enforce type stability of the integrand, so you should always pick the widest integration limit type so that inference works properly. For example, if [`ContQuadGKJL`](@ref) is used as an algorithm in the nested scheme, then the limits of integration should be made complex.
