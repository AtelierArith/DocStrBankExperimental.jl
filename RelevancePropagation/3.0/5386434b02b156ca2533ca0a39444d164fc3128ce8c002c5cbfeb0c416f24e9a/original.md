```
WSquareRule()
```

LRP-$w²$ rule. Commonly used on the first layer when values are unbounded.

# Definition

Propagates relevance $R^{k+1}$ at layer output to $R^k$ at layer input according to

$$
R_j^k = \sum_i\frac{W_{ij}^2}{\sum_l W_{il}^2} R_i^{k+1}
$$

# References

  * G. Montavon et al., *Explaining Nonlinear Classification Decisions with Deep Taylor Decomposition*
