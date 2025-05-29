```
mean_recurrence_time(x)
```

# Definitions

This is the expected number of steps for the process to return to state i given that the process started in state $i$.

# Arguments

  * `x`: some kind of Markov chain.

# Returns

A 1D array where the ith entry is the mean recurrence time of state $i$.

# Notes

`x` must be irreducible (i.e. ergodic).

# Examples

```jldoctest mean_recurrence_time
using DiscreteMarkovChains
T = [
    0.1 0.2 0.7;
    0.3 0.0 0.7;
    0.4 0.4 0.2;
]
X = DiscreteMarkovChain(T)

mean_recurrence_time(X)

# output

3-element Array{Float64,1}:
 3.4615384615384603
 4.090909090909091
 2.1428571428571432
```

If we have a reducible chain, then no error will be raised but the output will be nonsense.

```jldoctest mean_recurrence_time
T = [
    1.0 0.0 0.0;
    0.1 0.5 0.4;
    0.0 0.3 0.7;
]
X = DiscreteMarkovChain(T)

mean_recurrence_time(X)

# output

3-element Array{Float64,1}:
   1.0
 -Inf
 -Inf
```
