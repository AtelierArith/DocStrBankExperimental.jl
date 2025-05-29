```
is_regular(x)
```

# Definitions

A Markov chain is called a regular chain if some power of the transition matrix has only positive elements. This is equivalent to being ergodic and aperiodic.

# Arguments

  * `x`: some kind of discrete Markov chain.

# Returns

`true` if the Markov chain, `x`, is regular.

# Examples

We will set up a matrix with 2 communication classes and show that it is not regular.

```jldoctest is_regular
using DiscreteMarkovChains
T = [
    0 1 0;
    1 0 0;
    0 0 1;
]
X = DiscreteMarkovChain(T)

is_regular(X)

# output

false
```

Repeat the above but now all states communicate.

```jldoctest is_regular
T = [
    0.0 0.5 0.5;
    0.0 0.0 1.0;
    1.0 0.0 0.0;
]
X = DiscreteMarkovChain(T)

is_regular(X)

# output

true
```

Notice how a periodic chain is not regular even though there is only one communication class.

```jldoctest is_regular
T = [
    0 1 0;
    0 0 1;
    1 0 0;
]
X = DiscreteMarkovChain(T)

is_regular(X)

# output

false
```
