```
HMM([a, ]A, B) -> HMM
```

Build an HMM with transition matrix `A` and observation distributions `B`.   If the initial state distribution `a` is not specified, a uniform distribution is assumed. 

Observations distributions can be of different types (for example `Normal` and `Exponential`),   but they must be of the same dimension.

Alternatively, `B` can be an emission matrix where `B[i,j]` is the probability of observing symbol `j` in state `i`.

**Arguments**

  * `a::AbstractVector{T}`: initial probabilities vector.
  * `A::AbstractMatrix{T}`: transition matrix.
  * `B::AbstractVector{<:Distribution{F}}`: observations distributions.
  * or `B::AbstractMatrix`: emission matrix.

**Example**

```julia
using Distributions, HMMBase
# from distributions
hmm = HMM([0.9 0.1; 0.1 0.9], [Normal(0,1), Normal(10,1)])
# from an emission matrix
hmm = HMM([0.9 0.1; 0.1 0.9], [0. 0.5 0.5; 0.25 0.25 0.5])
```
