```
ContinuousMarkovChain(transition_matrix)
ContinuousMarkovChain(state_space, transition_matrix)
ContinuousMarkovChain(discrete_markov_chain)
```

Creates a new continuous Markov chain object. This is also known as a Markov jump process.

Note that an irreducible finite continuous-time Markov chain is always positive recurrent and its stationary distribution always exists, is unique and is equal to the limiting distribution.

# Arguments

  * `state_space`: The names of the states that make up the Markov chain.
  * `transition_matrix`: The transition intensity matrix. Also known as the generator matrix.
  * `discrete_markov_chain`: An instance of `DiscreteMarkovChain`.

# Examples

The following shows a basic Sunny-Cloudy-Rainy weather model.

```jldoctest ContinuousMarkovChain
using DiscreteMarkovChains
T = [
    -.1 0.1 0.0;
    0.5 -.8 0.3;
    0.1 0.4 -.5;
]
X = ContinuousMarkovChain(["Sunny", "Cloudy", "Rainy"], T)
println(state_space(X))

# output

["Sunny", "Cloudy", "Rainy"]
```

```jldoctest ContinuousMarkovChain
println(transition_matrix(X))

# output

[-0.1 0.1 0.0; 0.5 -0.8 0.3; 0.1 0.4 -0.5]
```

# References

1. [Wikipedia](https://en.wikipedia.org/wiki/Continuous-time_Markov_chain)
