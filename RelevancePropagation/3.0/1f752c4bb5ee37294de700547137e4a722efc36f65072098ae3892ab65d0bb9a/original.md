```
FlatRule()
```

LRP-Flat rule. Similar to the [`WSquareRule`](@ref), but with all weights set to one and all bias terms set to zero.

# Definition

Propagates relevance $R^{k+1}$ at layer output to $R^k$ at layer input according to

$$
R_j^k = \sum_i\frac{1}{\sum_l 1} R_i^{k+1} = \sum_i\frac{1}{n_i} R_i^{k+1}
$$

where $n_i$ is the number of input neurons connected to the output neuron at index $i$.

# References

  * S. Lapuschkin et al., *Unmasking Clever Hans predictors and assessing what machines really learn*
