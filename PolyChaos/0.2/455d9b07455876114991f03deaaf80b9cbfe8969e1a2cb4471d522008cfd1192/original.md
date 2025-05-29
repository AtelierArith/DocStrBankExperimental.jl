```
convert2affinePCE(mu::Real, sigma::Real, op::AbstractCanonicalOrthoPoly; kind::String)
```

Computes the affine PCE coefficients $x_0$ and $x_1$ from

$$
X = a_1 + a_2 \Xi = x_0 + x_1 \phi_1(\Xi),
$$

where $\phi_1(t) = t-\alpha_0$ is the first-order monic basis polynomial.

Works for subtypes of AbstractCanonicalOrthoPoly. The keyword `kind in ["lbub", "μσ"]` specifies whether `p1` and `p2` have the meaning of lower/upper bounds or mean/standard deviation.
