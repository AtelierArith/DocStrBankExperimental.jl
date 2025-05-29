```
Y = Weingarten(M::ProductManifold, p, X, V)
Weingarten!(M::ProductManifold, Y, p, X, V)
```

Since the metric decouples, also the computation of the Weingarten map $\mathcal W_p$ can be computed elementwise on the single elements of the [`ProductManifold`](@ref) `M`.
