```
communication_classes(x)
```

# Definitions

A state $j$ is accessible from state $i$ if it is possible to eventually reach state $j$ given that the process started in state $i$. That is, $∃ \, t ∈ \mathbb{N}$ such that $p^{(t)}_{i,j} > 0$.

States $i$ and $j$ communicate if $i$ is accessible from $j$ and $j$ is accessible from $i$.

A communication class is the set of states in a Markov chain that are all accessible from one another. Communication classes form a class in the mathematical sense. They also form a partition of the state space.

A state $i$ is recurrent if the process is guarenteed to eventually return to state $i$ given that the process started in state $i$. If a state $i$ is not recurrent, then it is said to be transient.

# Arguments

  * `x`: some kind of Markov chain.

# Returns

A tuple containing 2 arrays.

  * This first array contains C arrays which store the states that communicate.
  * The second array is an array of Bool where the ith value is true if the ith communication class is recurrent.

# Examples

```jldoctest communication_classes
using DiscreteMarkovChains
T = [
    1 0;
    0 1;
]
X = DiscreteMarkovChain(T)

communication_classes(X)

# output

([[1], [2]], Any[true, true])
```

So the Markov chain has two communication classes and both are recurrent.

```jldoctest communication_classes
T = [
    .5 .5 .0;
    .2 .8 .0;
    .1 .2 .7;
]
X = DiscreteMarkovChain(["Sunny", "Cloudy", "Rainy"], T)

communication_classes(X)

# output

([["Sunny", "Cloudy"], ["Rainy"]], Any[true, false])
```

So the Sunny and Cloudy states communicate and are recurrent. The Rainy state is transient. Note that this is not a very good weather model since once it stops raining, it will never rain again.
