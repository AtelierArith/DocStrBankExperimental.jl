```
permute_lefschetz_complex(lc::LefschetzComplex,
                          permutation::Vector{Int})
```

Permute the indices of a Lefschetz complex.

The vector `permutation` contains a permutation of the indices for the given Lefschetz complex `lc`. If no permutation is specified, or if the length of the vector is not correct, then a randomly generated one will be used. Note that the permutation has to respect the ordering of the cells by dimension, otherwise an error is raised. In other words,  the permutation has to decompose into permutations within each dimension. This is automatically done if no permutation is explicitly specified.
