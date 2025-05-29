```
ZeroRule()
```

LRP-$0$ rule. Commonly used on upper layers.

# Definition

Propagates relevance $R^{k+1}$ at layer output to $R^k$ at layer input according to

$$
R_j^k = \sum_i \frac{W_{ij}a_j^k}{\sum_l W_{il}a_l^k+b_i} R_i^{k+1}
$$

# References

  * S. Bach et al., *On Pixel-Wise Explanations for Non-Linear Classifier Decisions by Layer-Wise Relevance Propagation*
