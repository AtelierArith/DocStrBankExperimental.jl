```
GrassModel(; A_g, m_g=3)
```

Creates a Grass model to compute the sediment discharge `q_s` as

$$
q_s = A_g v^{m_g}
$$

with the coefficients `A_g` and `m_g`. The constant `A_g` lies in the interval $[0,1]$ and is a dimensional calibration constant that is usually measured experimentally. It expresses the kind of interaction between the fluid and the sediment, the strength of which increases as `A_g` approaches to 1. The factor `m_g` lies in the interval $[1, 4]$. Typically, one considers an odd integer value for `m_g` such that the sediment discharge `q_s` can be differentiated and the model remains valid for all values of the velocity `v`.

An overview of different formulations to compute the sediment discharge can be found in:

  * M.J. Castro Díaz, E.D. Fernández-Nieto, A.M. Ferreiro (2008)
    Sediment transport models in Shallow Water equations and numerical approach by high order finite volume methods
    [DOI:10.1016/j.compfluid.2007.07.017](https://doi.org/10.1016/j.compfluid.2007.07.017)
