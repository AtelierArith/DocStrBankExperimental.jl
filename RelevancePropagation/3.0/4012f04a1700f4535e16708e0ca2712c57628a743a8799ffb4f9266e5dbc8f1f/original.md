```
ZPlusRule()
```

LRP-$z⁺$ rule. Commonly used on lower layers.

Equivalent to `AlphaBetaRule(1.0f0, 0.0f0)`, but slightly faster. See also [`AlphaBetaRule`](@ref).

# Definition

Propagates relevance $R^{k+1}$ at layer output to $R^k$ at layer input according to

$$
R_j^k = \sum_i\frac{\left(W_{ij}a_j^k\right)^+}{\sum_l\left(W_{il}a_l^k+b_i\right)^+} R_i^{k+1}
$$

# References

  * S. Bach et al., *On Pixel-Wise Explanations for Non-Linear Classifier Decisions by Layer-Wise Relevance Propagation*
  * G. Montavon et al., *Explaining Nonlinear Classification Decisions with Deep Taylor Decomposition*
