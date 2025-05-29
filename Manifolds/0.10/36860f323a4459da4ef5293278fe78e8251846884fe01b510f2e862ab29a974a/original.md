```
exp(G::GeneralLinear, p, X)
```

Compute the exponential map on the [`GeneralLinear`](@ref) group.

The exponential map is

$$
\exp_p \colon X ↦ p \operatorname{Exp}(X^\mathrm{H}) \operatorname{Exp}(X - X^\mathrm{H}),
$$

where $\operatorname{Exp}(⋅)$ denotes the matrix exponential, and $⋅^\mathrm{H}$ is the conjugate transpose [AndruchowLarotondaRechtVarela:2014](@cite) [MartinNeff:2016](@cite).
