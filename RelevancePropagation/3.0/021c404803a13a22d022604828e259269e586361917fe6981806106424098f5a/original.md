```
AlphaBetaRule([alpha=2.0, beta=1.0])
```

LRP-$αβ$ rule. Weights positive and negative contributions according to the parameters `alpha` and `beta` respectively. The difference $α-β$ must be equal to one. Commonly used on lower layers.

# Definition

Propagates relevance $R^{k+1}$ at layer output to $R^k$ at layer input according to

$$
R_j^k = \sum_i\left(
    \alpha\frac{\left(W_{ij}a_j^k\right)^+}{\sum_l\left(W_{il}a_l^k+b_i\right)^+}
    -\beta\frac{\left(W_{ij}a_j^k\right)^-}{\sum_l\left(W_{il}a_l^k+b_i\right)^-}
\right) R_i^{k+1}
$$

# Optional arguments

  * `alpha`: Multiplier for the positive output term, defaults to `2.0`.
  * `beta`: Multiplier for the negative output term, defaults to `1.0`.

# References

  * S. Bach et al., *On Pixel-Wise Explanations for Non-Linear Classifier Decisions by Layer-Wise Relevance Propagation*
  * G. Montavon et al., *Layer-Wise Relevance Propagation: An Overview*
