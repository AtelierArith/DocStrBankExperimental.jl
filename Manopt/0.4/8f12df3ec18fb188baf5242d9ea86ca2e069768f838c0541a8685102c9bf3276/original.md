```
FrankWolfeCost{P,T}
```

A structure to represent the oracle sub problem in the [`Frank_Wolfe_method`](@ref). The cost function reads

$$
F(q) = ⟨X, \log_p q⟩
$$

The values `p` and `X` are stored within this functor and should be references to the iterate and gradient from within [`FrankWolfeState`](@ref).
