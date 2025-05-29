```
DiscreteMarkovChain(transition_matrix)
DiscreteMarkovChain(state_space, transition_matrix)
DiscreteMarkovChain(continuous_markov_chain)
```

Creates a new discrete Markov chain object.

# Arguments

  * `state_space`: The names of the states that make up the Markov chain.
  * `transition_matrix`: The single step transition probability matrix.
  * `continuous_markov_chain`: An instance of `ContinuousMarkovChain`.

# Examples

The following shows a basic Sunny-Cloudy-Rainy weather model.

```jldoctest DiscreteMarkovChain
using DiscreteMarkovChains
T = [
    0.9 0.1 0;
    0.5 0.2 0.3;
    0.1 0.4 0.5
]
X = DiscreteMarkovChain(["Sunny", "Cloudy", "Rainy"], T)
println(state_space(X))

# output

["Sunny", "Cloudy", "Rainy"]
```

```jldoctest DiscreteMarkovChain
println(transition_matrix(X))

# output

[0.9 0.1 0.0; 0.5 0.2 0.3; 0.1 0.4 0.5]
```

# References

1. [Wikipedia](https://en.wikipedia.org/wiki/Markov_chain#Discrete-time_Markov_chain)
2. [Dartmouth College](https://www.dartmouth.edu/~chance/teaching_aids/books_articles/probability_book/Chapter11.pdf)
