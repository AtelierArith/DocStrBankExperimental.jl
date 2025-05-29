```
CosineSimilarityBinning(; m::Int, τ::Int, nbins::Int)
```

A [`OutcomeSpace`](@ref) based on the cosine similarity [Wang2020](@cite).

It can be used with [`information`](@ref) to compute the "diversity entropy" of an input timeseries [Wang2020](@cite).

The implementation here allows for `τ != 1`, which was not considered in the original paper.

## Description

CosineSimilarityBinning probabilities are computed as follows.

1. From the input time series `x`, using embedding lag `τ` and embedding dimension `m`,  construct the embedding  $Y = \{\bf x_i \} = \{(x_{i}, x_{i+\tau}, x_{i+2\tau}, \ldots, x_{i+m\tau - 1}\}_{i = 1}^{N-mτ}$.
2. Compute $D = \{d(\bf x_t, \bf x_{t+1}) \}_{t=1}^{N-mτ-1}$,  where $d(\cdot, \cdot)$ is the cosine similarity between two `m`-dimensional  vectors in the embedding.
3. Divide the interval `[-1, 1]` into `nbins` equally sized subintervals (including the value `+1`).
4. Construct a histogram of cosine similarities $d \in D$ over those subintervals.
5. Sum-normalize the histogram to obtain probabilities.

## Outcome space

The outcome space for `CosineSimilarityBinning` is the bins of the `[-1, 1]` interval, and the return configuration is the same as in [`ValueBinning`](@ref) (left bin edge).

## Implements

  * [`codify`](@ref). Used for encoding inputs where ordering matters (e.g. time series).
