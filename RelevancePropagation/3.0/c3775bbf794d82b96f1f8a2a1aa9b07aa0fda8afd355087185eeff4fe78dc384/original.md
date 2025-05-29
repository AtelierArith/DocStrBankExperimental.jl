```
GeneralizedGammaRule([gamma=0.25])
```

Generalized LRP-$γ$ rule. Can be used on layers with `leakyrelu` activation functions.

# Definition

Propagates relevance $R^{k+1}$ at layer output to $R^k$ at layer input according to

$$
R_j^k = \sum_i\frac
    {(W_{ij}+\gamma W_{ij}^+)a_j^+ +(W_{ij}+\gamma W_{ij}^-)a_j^-}
    {\sum_l(W_{il}+\gamma W_{il}^+)a_j^+ +(W_{il}+\gamma W_{il}^-)a_j^- +(b_i+\gamma b_i^+)}
I(z_k>0) \cdot R^{k+1}_i
+\sum_i\frac
    {(W_{ij}+\gamma W_{ij}^-)a_j^+ +(W_{ij}+\gamma W_{ij}^+)a_j^-}
    {\sum_l(W_{il}+\gamma W_{il}^-)a_j^+ +(W_{il}+\gamma W_{il}^+)a_j^- +(b_i+\gamma b_i^-)}
I(z_k<0) \cdot R^{k+1}_i
$$

# Optional arguments

  * `gamma`: Optional multiplier for added positive weights, defaults to `0.25`.

# References

  * L. Andéol et al., *Learning Domain Invariant Representations by Joint Wasserstein Distance Minimization*
