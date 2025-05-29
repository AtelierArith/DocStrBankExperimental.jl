```
StopWhenGradientChangeLess <: StoppingCriterion
```

A stopping criterion based on the change of the gradient

```
\lVert \mathcal T_{p^{(k)}\gets p^{(k-1)} \operatorname{grad} f(p^{(k-1)}) -  \operatorname{grad} f(p^{(k-1)}) \rVert < ε
```

# Constructor

```
StopWhenGradientChangeLess(
    M::AbstractManifold,
    ε::Float64;
    storage::StoreStateAction=StoreStateAction([:Iterate]),
    vector_transport_method::IRT=default_vector_transport_method(M),
)
```

Create a stopping criterion with threshold `ε` for the change gradient, that is, this criterion indicates to stop when [`get_gradient`](@ref) is in (norm of) its change less than `ε`, where `vector_transport_method` denotes the vector transport $\mathcal T$ used.
