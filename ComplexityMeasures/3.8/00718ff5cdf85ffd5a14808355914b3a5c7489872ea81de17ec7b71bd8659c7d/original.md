```
WeightedOrdinalPatterns <: OutcomeSpace
WeightedOrdinalPatterns{m}(τ = 1, lt::Function = ComplexityMeasures.isless_rand)
```

A variant of [`OrdinalPatterns`](@ref) that also incorporates amplitude information, based on the weighted permutation entropy [Fadlallah2013](@cite). The outcome space and arguments are the same as in [`OrdinalPatterns`](@ref).

## Description

For each ordinal pattern extracted from each state (or delay) vector, a weight is attached to it which is the variance of the vector. Probabilities are then estimated by summing the weights corresponding to the same pattern, instead of just counting the occurrence of the same pattern.

!!! note "An implementation note"
    *Note: in equation 7, section III, of the original paper, the authors write*

    $$
    w_j = \dfrac{1}{m}\sum_{k=1}^m (x_{j-(k-1)\tau} - \mathbf{\hat{x}}_j^{m, \tau})^2.
    $$

    *But given the formula they give for the arithmetic mean, this is **not** the variance of the delay vector $\mathbf{x}_i$, because the indices are mixed: $x_{j+(k-1)\tau}$ in the weights formula, vs. $x_{j+(k+1)\tau}$ in the arithmetic mean formula. Here, delay embedding and computation of the patterns and their weights are completely separated processes, ensuring that we compute the arithmetic mean correctly for each vector of the input dataset (which may be a delay-embedded timeseries).

