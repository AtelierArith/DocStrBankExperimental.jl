```
is_absorbing(x)
```

# Definitions

A Markov chain is absorbing if it has at least one absorbing state, and if from every state it is possible to go to an absorbing state (not necessarily in one step).

# Arguments

  * `x`: some kind of Markov chain.

# Returns

`true` if the Markov chain, `x`, is an absorbing chain. So the process is guarenteed to be absorbed eventually.

# Examples

The following is a typical example of an absorbing chain.

```jldoctest is_absorbing
using DiscreteMarkovChains
T = [
    1.0 0.0 0.0;
    0.1 0.8 0.1;
    0.0 0.3 0.7;
]
X = DiscreteMarkovChain(T)

is_absorbing(X)

# output

true
```

If a Markov chain does not have an absorbing state then the chain is not absorbing. The converse is not true as we will see soon.

```jldoctest is_absorbing
T = [
    0.5 0.5 0.0;
    0.5 0.0 0.5;
    0.0 0.5 0.5;
]
X = DiscreteMarkovChain(T)

is_absorbing(X)

# output

false
```

In the following, the chain has multiple absorbing states but the process is not guarenteed to be absorbed into those states.

```jldoctest is_absorbing
T = [
    1 0 0 0;
    0 1 0 0;
    0 0 0 1;
    0 0 1 0;
]
X = DiscreteMarkovChain(T)

is_absorbing(X)

# output

false
```

# References

1. [Dartmouth College](https://www.dartmouth.edu/~chance/teaching_aids/books_articles/probability_book/Chapter11.pdf)
