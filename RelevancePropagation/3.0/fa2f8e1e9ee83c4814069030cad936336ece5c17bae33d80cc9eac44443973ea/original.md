```
ZBoxRule(low, high)
```

LRP-$zᴮ$-rule. Commonly used on the first layer for pixel input.

The parameters `low` and `high` should be set to the lower and upper bounds of the input features, e.g. `0.0` and `1.0` for raw image data. It is also possible to provide two arrays of that match the input size.

# Definition

Propagates relevance $R^{k+1}$ at layer output to $R^k$ at layer input according to

$$
R_j^k=\sum_i \frac{W_{ij}a_j^k - W_{ij}^{+}l_j - W_{ij}^{-}h_j}
    {\sum_l W_{il}a_l^k+b_i - \left(W_{il}^{+}l_l+b_i^{+}\right) - \left(W_{il}^{-}h_l+b_i^{-}\right)} R_i^{k+1}
$$

# References

  * G. Montavon et al., *Layer-Wise Relevance Propagation: An Overview*
