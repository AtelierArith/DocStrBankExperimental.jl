```
mean_first_passage_time(x)
```

# Definitions

This is the expected number of steps for the process to reach state $j$ given that the process started in state $i$. We say that the mean first passage time between a state and itself is 0.

# Arguments

  * `x`: some kind of Markov chain.

# Returns

A matrix where the $(i,j)$th entry is the mean recurrence time of state $i$. Diagonal elements are 0. The diagonals would have represented the mean recurrence time.

# Notes

`x` must be irreducible (i.e. ergodic).

# Examples

```jldoctest mean_first_passage_time
using DiscreteMarkovChains
T = [
    0.1 0.2 0.7;
    0.3 0.0 0.7;
    0.4 0.4 0.2;
]
X = DiscreteMarkovChain(T)

mean_first_passage_time(X)

# output

3×3 Array{Float64,2}:
 0.0      3.40909  1.42857
 2.88462  0.0      1.42857
 2.69231  2.95455  0.0
```

If we have a reducible chain, then no error will be raised but the output will be nonsense.

```jldoctest mean_first_passage_time
T = [
    1.0 0.0 0.0;
    0.1 0.5 0.4;
    0.0 0.3 0.7;
]
X = DiscreteMarkovChain(T)

mean_first_passage_time(X)

# output

3×3 Array{Float64,2}:
  0.0     -Inf  -Inf
 23.3333  NaN   -Inf
 26.6667  -Inf  NaN
```
