```
exp(M::EssentialManifold, p, X)
```

Compute the exponential map on the [`EssentialManifold`](@ref) from `p` into direction `X`, i.e.

$$
\text{exp}_p(X) =\text{exp}_g( \tilde X),  \quad g \in \text(SO)(3)^2,
$$

where $\tilde X$ is the horizontal lift of $X$[TronDaniilidis:2017](@cite).
