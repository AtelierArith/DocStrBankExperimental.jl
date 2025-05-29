```
FrankWolfeGradient{P,T}
```

A structure to represent the gradient of the oracle sub problem in the [`Frank_Wolfe_method`](@ref), that is for a given point `p` and a tangent vector `X` the function reads

$$
F(q) = ⟨X, \log_p q⟩
$$

Its gradient can be computed easily using `adjoint_differential_log_argument`.

The values `p` and `X` are stored within this functor and should be references to the iterate and gradient from within [`FrankWolfeState`](@ref).
