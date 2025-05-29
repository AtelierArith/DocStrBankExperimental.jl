```
LempelZiv76 <: ComplexityEstimator
LempelZiv76()
```

The Lempel-Ziv, or `LempelZiv76`, complexity measure [LempelZiv1976](@cite), which is used with [`complexity`](@ref) and [`complexity_normalized`](@ref).

For results to be comparable across sequences with different length, use the normalized version. Normalized `LempelZiv76`-complexity is implemented as given in [Amigó2004](@citet). The normalized measure is close to zero for very regular signals, while for random sequences, it is close to 1 with high probability[^Amigó2004]. Note: the normalized `LempelZiv76` complexity can be higher than 1[^Amigó2004].

The `LempelZiv76` measure applies only to binary sequences, i.e. sequences with a two-element alphabet (precisely two distinct outcomes). For performance optimization, we do not check the number of unique elements in the input. If your input sequence is not binary, you must [`encode`](@ref) it first using one of the implemented [`Encoding`](@ref) schemes (or encode your data manually).
