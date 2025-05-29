```
GenericSymmetry(f, L)
```

Allows a user-defined symmetry. Just provide a function to transform a binary basis index and the order of the symmetry.

# Fields

  * `f::Function`: transformation of the indices given in binary representation (0:2^N-1)
  * `L::Int`: order of the symmetry, i.e. the smallest positive number such that f^L = identity
