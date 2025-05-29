```
canonical_form(x)
```

Reorders the states of the transition matrix of `x` so that recurrent states appear first and transient states appear last.

# Arguments

  * `x`: some kind of Markov chain.

# Returns

A tuple with the new states and the new transition matrix.

# Examples

We will use the same matrix as previous examples but change the order of it.

```jldoctest canonical_form
using DiscreteMarkovChains
T = [
    0.7 0.2 0.1;
    0.0 0.0 1.0;
    0.0 1.0 0.0;
]
X = DiscreteMarkovChain(["Rainy", "Cloudy", "Sunny"], T)

canonical_form(X)

# output

(Any["Cloudy", "Sunny", "Rainy"], [0.0 1.0 0.0; 1.0 0.0 0.0; 0.2 0.1 0.7])
```

Here, Cloudy and Sunny are recurrent states so they appear first. Rainy is a transient state so it appears last.
