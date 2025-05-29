```
fundamental_matrix(x)
```

# Definitions

The fundamental matrix of a markov chain is defined to be $(I-C)^{-1}$ where $C$ is the sub-transition matrix that takes transient states to transient states.

The $(i, j)$th entry of the fundamental matrix is the expected number of times the chain is in state $j$ over the whole process given that the chain started in state $i$.

# Arguments

  * `x`: some kind of Markov chain.

# Returns

The fundamental matrix of the Markov chain.

# Notes

It is advised to have `x` in canonical form already. This is to avoid confusion of what states make up each element of the array ouput.

# Examples

Here is a typical example of the fundamental matrix.

```jldoctest fundamental_matrix
using DiscreteMarkovChains
T = [
    1.0 0.0 0.0;
    0.0 0.4 0.6;
    0.2 0.2 0.6;
]
X = DiscreteMarkovChain(T)

fundamental_matrix(X)

# output

2×2 Array{Float64,2}:
 3.33333  5.0
 1.66667  5.0
```

If the chain is ergodic, then the fundamental matrix is a 0x0 matrix (since there are no transient states).

```jldoctest fundamental_matrix
T = [
    0.0 1.0 0.0;
    0.5 0.0 0.5;
    0.0 1.0 0.0;
]
X = DiscreteMarkovChain(T)

fundamental_matrix(X)

# output

0×0 Array{Any,2}
```
