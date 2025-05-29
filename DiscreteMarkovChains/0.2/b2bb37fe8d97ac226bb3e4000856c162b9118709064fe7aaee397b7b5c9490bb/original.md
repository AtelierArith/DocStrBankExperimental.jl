```
is_ergodic(x)
```

# Definitions

A Markov chain is called an ergodic chain if it is possible to go from every state to every state (not necessarily in one move). That is, every state communicates and the whole tranistion matrix forms one communication class.

In many books, ergodic Markov chains are called irreducible.

If a Markov chain is not irreducible then it is reducible. This means that the Markov chain can be broken down into smaller irreducible chains that do not communicate. One chain might still be accessible from another though.

# Arguments

  * `x`: some kind of Markov chain.

# Returns

`true` if the Markov chain, `x`, is ergodic. This is, if every state can be accessed from every other state. Another term for this is irreducible.

# Examples

We will set up a matrix with 2 communication classes and show that it is not ergodic.

```jldoctest is_ergodic
using DiscreteMarkovChains
T = [
    0 1 0;
    1 0 0;
    0 0 1;
]
X = DiscreteMarkovChain(T)

is_ergodic(X)

# output

false
```

Repeat the above but now all states communicate.

```jldoctest is_ergodic
T = [
    0.0 0.5 0.5;
    0.0 0.0 1.0;
    1.0 0.0 0.0;
]
X = DiscreteMarkovChain(T)

is_ergodic(X)

# output

true
```

Notice how a periodic chain is regular no matter the periodicity.

```jldoctest is_ergodic
T = [
    0 1 0;
    0 0 1;
    1 0 0;
]
X = DiscreteMarkovChain(T)

is_ergodic(X)

# output

true
```
