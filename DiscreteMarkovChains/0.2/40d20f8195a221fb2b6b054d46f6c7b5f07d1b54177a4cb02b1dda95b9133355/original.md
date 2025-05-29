```
first_passage_probabilities(x, t, i=missing, j=missing)
```

# Definitions

This is the probability that the process enters state $j$ for the first time at time $t$ given that the process started in state $i$ at time 0. That is, $f^{(t)}_{i,j}$. If no `i` or `j` is given, then it will return a matrix instead with entries $f^{(t)}_{i,j}$ for `i` and `j` in the state space of `x`.

# Why Do We Use A Slow Algorithm?

So that `t` can be symbolic if nessesary. That is, if symbolic math libraries want to use this library, it will pose no hassle.

# Arguments

  * `x`: some kind of Markov chain.
  * `t`: the time to calculate the first passage probability.
  * `i`: the state that the prcess starts in.
  * `j`: the state that the process must reach for the first time.

# Returns

A scalar value or a matrix depending on whether `i` and `j` are given.

# Examples

```jldoctest first_passage_probabilities
using DiscreteMarkovChains
T = [
    0.1 0.9;
    0.3 0.7;
]
X = DiscreteMarkovChain(T)

first_passage_probabilities(X, 2)

# output

2×2 Array{Float64,2}:
 0.27  0.09
 0.21  0.27
```

If `X` has a custom state space, then `i` and `j` must be in that state space.

```jldoctest first_passage_probabilities
T = [
    0.1 0.9;
    0.3 0.7;
]
X = DiscreteMarkovChain(["Sunny", "Rainy"], T)

first_passage_probabilities(X, 2, "Sunny", "Rainy")

# output

0.09000000000000001
```

Notice how this is the (1, 2) entry in the first example.

# References

1. [University of Windsor](https://scholar.uwindsor.ca/cgi/viewcontent.cgi?article=1125&context=major-papers)
2. [Durham University](http://maths.dur.ac.uk/stats/courses/ProbMC2H/_files/handouts/1516MarkovChains2H.pdf)
