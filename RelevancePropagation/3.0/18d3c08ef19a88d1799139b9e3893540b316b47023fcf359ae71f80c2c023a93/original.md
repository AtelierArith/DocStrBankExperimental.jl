```
EpsilonRule([epsilon=1.0e-6])
```

LRP-$ϵ$ rule. Commonly used on middle layers.

# Definition

Propagates relevance $R^{k+1}$ at layer output to $R^k$ at layer input according to

$$
R_j^k = \sum_i\frac{W_{ij}a_j^k}{\epsilon +\sum_{l}W_{il}a_l^k+b_i} R_i^{k+1}
$$

# Optional arguments

  * `epsilon`: Optional stabilization parameter, defaults to `1.0e-6`.

# References

  * S. Bach et al., *On Pixel-Wise Explanations for Non-Linear Classifier Decisions by Layer-Wise Relevance Propagation*
