```
stationary_distribution(x)
```

# Definitions

A stationary distribution of a Markov chain is a probability distribution that remains unchanged in the Markov chain as time progresses. It is a row vector, $w$ such that its elements sum to 1 and it satisfies $wT = w$. $T$ is the one-step transiton matrix of the Markov chain.

In other words, $w$ is invariant by the matrix $T$.

For simplicity, this function returns a column vector instead of a row vector.

For continuous Markov chains, the stationary_distribution is given by the solution to $wQ = 0$ where $Q$ is the transition intensity matrix.

# Arguments

  * `x`: some kind of Markov chain.

# Returns

A column vector, $w$, that satisfies the equation $w'T = w'$.

# Examples

The stationary distribution will always exist. However, it might not be unique.

If it is unique there are no problems.

```jldoctest stationary_distribution
using DiscreteMarkovChains
T = [
    4 2 4;
    1 0 9;
    3 5 2;
]//10
X = DiscreteMarkovChain(T)

stationary_distribution(X)

# output

3-element Array{Rational{Int64},1}:
 35//129
 12//43
 58//129
```

If there are infinite solutions then the principle solution is taken (every free variable is set to 0). A Moore-Penrose inverse is used.

```jldoctest stationary_distribution
T = [
    0.4 0.6 0.0;
    0.6 0.4 0.0;
    0.0 0.0 1.0;
]
X = DiscreteMarkovChain(T)

stationary_distribution(X)

# output

3-element Array{Float64,1}:
 0.33333333333333337
 0.33333333333333337
 0.33333333333333337
```

# References

1. [Brilliant.org](https://brilliant.org/wiki/stationary-distributions/#:~:text=A%20stationary%20distribution%20of%20a,transition%20matrix%20P%2C%20it%20satisfies)
