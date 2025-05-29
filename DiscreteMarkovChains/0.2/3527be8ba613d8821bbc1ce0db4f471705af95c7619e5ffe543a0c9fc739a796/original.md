```
exit_probabilities(x)
```

# Arguments

  * `x`: some kind of Markov chain.

# Returns

An array where element $(i, j)$ is the probability that transient state $i$ will enter recurrent state $j$ on its first step out of the transient states. That is, $e_{i,j}$.

# Examples

The following should be fairly obvious. States 1, 2 and 3 are the recurrent states and state 4 is the single transient state that must enter one of these 3 on the next time step. There is no randomness at play here.

```jldoctest exit_probabilities
using DiscreteMarkovChains
T = [
    0.2 0.2 0.6 0.0;
    0.5 0.4 0.1 0.0;
    0.6 0.2 0.2 0.0;
    0.2 0.3 0.5 0.0;
]
X = DiscreteMarkovChain(T)

exit_probabilities(X)

# output

1×3 Array{Float64,2}:
 0.2  0.3  0.5
```

So state 4 has probabilities 0.2, 0.3 and 0.5 of reaching states 1, 2 and 3 respectively on the first step out of the transient states (consisting only of state 4).

The following is less obvious.

```jldoctest exit_probabilities
T = [
    1.0 0.0 0.0 0.0;
    0.0 1.0 0.0 0.0;
    0.1 0.3 0.3 0.3;
    0.2 0.3 0.4 0.1;
]
X = DiscreteMarkovChain(T)

exit_probabilities(X)

# output

2×2 Array{Float64,2}:
 0.294118  0.705882
 0.352941  0.647059
```

So state 3 has a 29% chance of entering state 1 on the first time step out (and the remaining 71% chance of entering state 2). State 4 has a 35% chance of reaching state 1 on the first time step out.
