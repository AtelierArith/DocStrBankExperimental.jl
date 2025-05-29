```
overlapwithcomputational(pstr::PauliString, onebitinds)
```

Calculates the overlap of a Pauli string with the computational basis state which has one-bits at all specified `onebitinds` and zero-bits elsewhere. For example, `overlapwithcomputational(pstr, [1,2,4])` returns the overlap with `|1101000...>` and will be either zero or plus/minus `pstr.coeff`.
