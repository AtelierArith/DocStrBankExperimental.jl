```
info.αbest
AMORS.best_scaling_factor(info::AMORS.Info)
AMORS.best_scaling_factor(μ, J(x), q, ν, K(y), r)
AMORS.best_scaling_factor(μ*J(x), q, ν*K(y), r)
```

yield the best scaling factor defined by:

```
α⁺ = argmin_{α > 0} μ*J(α*x) + ν*K(y/α)
```

and which has a closed-form expression:

```
α⁺ = ((r*ν*K(y))/(q*μ*J(x)))^(1/(q + r))
```

The arguments are the values of the homogeneous functions, `J(x)` and `K(y)`, their respective multiplier, `μ` and `ν`, and their respective degrees `q = deg(J)` and `r = deg(K)` for the current estimates of the variables `x` and `y` of a bilinear model. All these arguments may be provided by AMORS algorithm state `info`.
