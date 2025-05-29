```
overlapwithcomputational(psum::PauliSum, onebitinds)
```

Calculates the overlap of a Pauli sum with the computational basis state which has one-bits at all specified `indices` and zero-bits elsewhere. For example, `overlapwithcomputational(psum, [1,2,4])` returns the overlap with `|1101000...>`
