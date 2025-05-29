```
GammaRule([gamma=0.25])
```

LRP-$γ$ rule. Commonly used on lower layers.

# Definition

Propagates relevance $R^{k+1}$ at layer output to $R^k$ at layer input according to

$$
R_j^k = \sum_i\frac{(W_{ij}+\gamma W_{ij}^+)a_j^k}
    {\sum_l(W_{il}+\gamma W_{il}^+)a_l^k+(b_i+\gamma b_i^+)} R_i^{k+1}
$$

# Optional arguments

  * `gamma`: Optional multiplier for added positive weights, defaults to `0.25`.

# References

  * G. Montavon et al., *Layer-Wise Relevance Propagation: An Overview*
