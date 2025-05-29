```
AbstractLocalModel
```

Supertype of methods for making a prediction of a query point `q` using local models, following the methods of [1]. Concrete subtypes are `AverageLocalModel` and `LinearLocalModel`.

All models weight neighbors with a chosen function, so that distant neighbors have smaller impact on the prediction and so that the interpolation is smooth. The default weighting function we use is

$$
\begin{aligned}
ω_i(d_i,d_{max}) = \left[ 1- \left(\frac{d_i}{d_{max}}\right)^2\right]^4
\end{aligned}
$$

with $d_i = ||x_{nn,i} -q||_2$ being the distance of each neighbor from the query point.

You can also provide your own function or give `ω_safe(d, dmax) = dmax > 0 ? (1.1 - (d/dmax)^2)^4 : 1.0` for a safe version of $ω$ that takes into acount edge cases. Finally you can also give `nothing` in place of `ω`. In that case no weighting is done and direct average of neighbors is returned.

### Average Local Model

```
AverageLocalModel(ω)
```

The prediction is simply the weighted average of the images $y_{nn, i}$ of the neighbors $x_{nn, i}$ of the query point `q`, weighting using given function `ω`

$$
\begin{aligned}
y_{pred} = \frac{\sum{\omega_i y_{nn,i}}}{\sum{\omega_i}}
\end{aligned}
$$

### Linear Local Model

```
LinearLocalModel([ω ], μ::Real=2.])
LinearLocalModel([ω ], s_min::Real, s_max::Real)
```

The prediction is a weighted linear regression over the neighbors $x_{nn, i}$ of the query and their images $y_{nn,i}$ as shown in [1].

Giving either `μ` or `s_min` and `s_max` determines which type of regularization is applied.

  * `μ` : Ridge Regression

    $$
    \begin{aligned}
    f(\sigma) = \frac{\sigma^2}{\mu^2 + \sigma^2}
    \end{aligned}
    $$
  * `s_min`, `s_max` : Soft Threshold

    $$
    \begin{aligned}
    f(\sigma) = \begin{cases} 0, & \sigma < s_{min}\\
    \left(1 - \left( \frac{s_{max}-\sigma}{s_{max}-s_{min}}\right)^2 \right)^2,
    &s_{min} \leq \sigma \leq s_{max} \\
    1, & \sigma > s_{max}\end{cases}
    \end{aligned}
    $$

## References

[1] : D. Engster & U. Parlitz, *Handbook of Time Series Analysis* Ch. 1, VCH-Wiley (2006)
