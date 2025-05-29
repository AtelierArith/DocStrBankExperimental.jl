```
Permutation
```

  * `Permutation(list)` creates a new `Permutation`. Here `list` must be a rearrangement of `1:n`.
  * `Permutation(n)` creates the identity `Permutation` of `1:n`.
  * `Permutation(n,k)` creates the `k`'th `Permutation` of `1:n`.
  * `Permutation(P::Matrix{Int})` creates a `Permutation` from a permutation matrix.
  * `Permutation(cycles::Vector{Vector{Int}})` creates a `Permutation` from a list of disjoint cycles.
