decomposition(Q)

# Description

```
Decompose Generator Matrix Q into a reverible and volume preserving component.
```

# Arguments

  * `Q::Matrix`: The generator matrix or transition matrix.

# Returns

  * (; exit_probabilities, rates)::NamedTuple: The exit probabilities and rates of the generator matrix.
