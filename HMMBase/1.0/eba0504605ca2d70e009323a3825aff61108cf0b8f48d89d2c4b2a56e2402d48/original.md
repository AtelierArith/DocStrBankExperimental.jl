```
forward(a, A, LL) -> (Vector, Float)
```

Compute forward probabilities using samples likelihoods. See [Forward-backward algorithm](https://en.wikipedia.org/wiki/Forward–backward_algorithm).

**Output**

  * `Vector{Float64}`: forward probabilities.
  * `Float64`: log-likelihood of the observed sequence.
