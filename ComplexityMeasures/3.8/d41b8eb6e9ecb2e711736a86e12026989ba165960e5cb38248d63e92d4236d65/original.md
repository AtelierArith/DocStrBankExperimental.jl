```
Dispersion(; c = 5, m = 2, τ = 1, check_unique = true)
```

An [`OutcomeSpace`](@ref) based on dispersion patterns, originally used by [Rostaghi2016](@citet) to compute the "dispersion entropy", which characterizes the complexity and irregularity of a time series.

Recommended parameter values [Li2018](@cite) are `m ∈ [2, 3]`, `τ = 1` for the embedding, and `c ∈ [3, 4, …, 8]` categories for the Gaussian symbol mapping.

## Description

Assume we have a univariate time series $X = \{x_i\}_{i=1}^N$. First, this time series is encoded into a symbol timeseries $S$ using the Gaussian encoding [`GaussianCDFEncoding`](@ref) with empirical mean `μ` and empirical standard deviation `σ` (both determined from $X$), and `c` as given to `Dispersion`.

Then, $S$ is embedded into an $m$-dimensional time series, using an embedding lag of $\tau$, which yields a total of $N - (m - 1)\tau$ delay vectors $z_i$, or "dispersion patterns". Since each element of $z_i$ can take on `c` different values, and each delay vector has `m` entries, there are `c^m` possible dispersion patterns. This number is used for normalization when computing dispersion entropy.

The returned probabilities are simply the frequencies of the unique dispersion patterns present in $S$ (i.e., the [`UniqueElements`](@ref) of $S$).

## Outcome space

The outcome space for `Dispersion` is the unique delay vectors whose elements are the the symbols (integers) encoded by the Gaussian CDF, i.e., the unique elements of $S$.

## Data requirements and parameters

The input must have more than one unique element for the Gaussian mapping to be well-defined. [Li2018](@citet) recommends that `x` has at least 1000 data points.

If `check_unique == true` (default), then it is checked that the input has more than one unique value. If `check_unique == false` and the input only has one unique element, then a `InexactError` is thrown when trying to compute probabilities.

!!! note "Why 'dispersion patterns'?"
    Each embedding vector is called a "dispersion pattern". Why? Let's consider the case when $m = 5$ and $c = 3$, and use some very imprecise terminology for illustration:

    When $c = 3$, values clustering far below mean are in one group, values clustered around the mean are in one group, and values clustering far above the mean are in a third group. Then the embedding vector $[2, 2, 2, 2, 2]$ consists of values that are close together (close to the mean), so it represents a set of numbers that are not very spread out (less dispersed). The embedding vector $[1, 1, 2, 3, 3]$, however, represents numbers that are much more spread out (more dispersed), because the categories representing "outliers" both above and below the mean are represented, not only values close to the mean.


For a version of this estimator that can be used on high-dimensional arrays, see [`SpatialDispersion`](@ref).

## Implements

  * [`codify`](@ref). Used for encoding inputs where ordering matters (e.g. time series).
