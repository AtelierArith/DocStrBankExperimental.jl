```
TransferOperator <: OutcomeSpace
TransferOperator(b::AbstractBinning; warn_precise = true, rng = Random.default_rng())
```

An [`OutcomeSpace`](@ref) based on binning data into rectangular boxes dictated by the given binning scheme `b`.

When used with [`probabilities`](@ref), then the transfer (Perron-Frobenius) operator is approximated over the bins, then bin probabilities are estimated as the invariant measure associated with that transfer operator. Assumes that the input data are sequential (time-ordered).

This implementation follows the grid estimator approach in [Diego2019](@citet).

## Precision

The default behaviour when using [`RectangularBinning`](@ref) or [`FixedRectangularBinning`](@ref) is to accept some loss of precision on the  bin boundaries for speed-ups, but this may lead to issues for `TransferOperator` where some points may be encoded as the symbol `-1` ("outside the binning"). The `warn_precise` keyword controls whether the user is warned when a less  precise binning is used.

## Outcome space

The outcome space for `TransferOperator` is the set of unique bins constructed from `b`. Bins are identified by their left (lowest-value) corners, are given in data units, and are returned as `SVector`s.

## Bin ordering

Bins returned by [`probabilities_and_outcomes`](@ref) are ordered according to first appearance (i.e. the first time the input (multivariate) timeseries visits the bin). Thus, if

```julia
b = RectangularBinning(4)
est = TransferOperator(b)
probs, outcomes = probabilities_and_outcomes(x, est) # x is some timeseries
```

then `probs[i]` is the invariant measure (probability) of the bin `outcomes[i]`, which is the `i`-th bin visited by the timeseries with nonzero measure.

## Description

The transfer operator $P^{N}$is computed as an `N`-by-`N` matrix of transition probabilities between the states defined by the partition elements, where `N` is the number of boxes in the partition that is visited by the orbit/points.

If  $\{x_t^{(D)} \}_{n=1}^L$ are the $L$ different $D$-dimensional points over which the transfer operator is approximated, $\{ C_{k=1}^N \}$ are the $N$ different partition elements (as dictated by `ϵ`) that gets visited by the points, and  $\phi(x_t) = x_{t+1}$, then

$$
P_{ij} = \dfrac
{\#\{ x_n | \phi(x_n) \in C_j \cap x_n \in C_i \}}
{\#\{ x_m | x_m \in C_i \}},
$$

where $\#$ denotes the cardinal. The element $P_{ij}$ thus indicates how many points that are initially in box $C_i$ end up in box $C_j$ when the points in $C_i$ are projected one step forward in time. Thus, the row $P_{ik}^N$ where $k \in \{1, 2, \ldots, N \}$ gives the probability of jumping from the state defined by box $C_i$ to any of the other $N$ states. It follows that $\sum_{k=1}^{N} P_{ik} = 1$ for all $i$. Thus, $P^N$ is a row/right stochastic matrix.

### Invariant measure estimation from transfer operator

The left invariant distribution $\mathbf{\rho}^N$ is a row vector, where $\mathbf{\rho}^N P^{N} = \mathbf{\rho}^N$. Hence, $\mathbf{\rho}^N$ is a row eigenvector of the transfer matrix $P^{N}$ associated with eigenvalue 1. The distribution $\mathbf{\rho}^N$ approximates the invariant density of the system subject to `binning`, and can be taken as a probability distribution over the partition elements.

In practice, the invariant measure $\mathbf{\rho}^N$ is computed using [`invariantmeasure`](@ref), which also approximates the transfer matrix. The invariant distribution is initialized as a length-`N` random distribution which is then applied to $P^{N}$. For reproducibility in this step, set the `rng`. The resulting length-`N` distribution is then applied to $P^{N}$ again. This process repeats until the difference between the distributions over consecutive iterations is below some threshold.

See also: [`RectangularBinning`](@ref), [`FixedRectangularBinning`](@ref), [`invariantmeasure`](@ref).
