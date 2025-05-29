```
exit_rate(Q)
```

# Description

```
Decompose Generator Matrix Q into exit probabilities, E, and rates, R, such that Q = ER
```

# Arguments

  * `Q::Matrix`: The generator matrix or transition matrix.

# Returns

  * (; exit_probabilities, rates)::NamedTuple: The exit probabilities and rates of the generator matrix.
