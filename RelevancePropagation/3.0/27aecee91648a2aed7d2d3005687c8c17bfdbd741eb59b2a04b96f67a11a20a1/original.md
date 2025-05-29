```
LayerNormRule()
```

LRP-LN rule. Used on `LayerNorm` layers.

# Definition

Propagates relevance $R^{k+1}$ at layer output to $R^k$ at layer input according to

$$
R_i^k = \sum_j\frac{a_i^k\left(\delta_{ij} - 1/N\right)}{\sum_l a_l^k\left(\delta_{lj}-1/N\right)} R_j^{k+1}
$$

Relevance through the affine transformation is by default propagated using the [`ZeroRule`](@ref).

If you would like to assign a special rule to the affine transformation inside of the `LayerNorm` layer, call `canonize` on your model. This will split the `LayerNorm` layer into

1. a `LayerNorm` layer without affine transformation
2. a `Scale` layer implementing the affine transformation

You can then assign separate rules to these two layers.

# References

  * A. Ali et al., *XAI for Transformers: Better Explanations through Conservative Propagation*
