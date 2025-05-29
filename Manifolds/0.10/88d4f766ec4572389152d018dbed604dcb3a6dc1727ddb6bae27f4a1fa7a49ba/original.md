```
inner(M::Hyperbolic, p, X, Y)
inner(M::Hyperbolic, p::HyperboloidPoint, X::HyperboloidTangentVector, Y::HyperboloidTangentVector)
```

Cmpute the inner product in the Hyperboloid model, i.e. the [`minkowski_metric`](@ref) in the embedding. The formula reads

$$
g_p(X,Y) = ⟨X,Y⟩_{\mathrm{M}} = -X_{n}Y_{n} + \displaystyle\sum_{k=1}^{n-1} X_kY_k.
$$

This employs the metric of the embedding, see [`Lorentz`](@ref) space, see for example the extended version [BergmannPerschSteidl:2015:1](@cite) of the paper [BergmannPerschSteidl:2016:1](@cite).
