```
hadamard(n)
```

Return a Hadamard matrix of order `n`.  The known Hadamard matrices up to size 256 are currently supported (via a lookup table), along with any size that factorizes into products of these known sizes and/or powers of two.

The return value is a matrix of `Int8` values. If you want to do further matrix computations with this matrix, you may want to convert to `Float64` first via `float(hadamard(n))`.

You can pretty-print a Hadamard matrix as a table of `+` and `-` (indicating the signs of the entries) via `Hadamard.printsigns`, e.g. `Hadamard.printsigns(hadamard(28))` for the 28×28 Hadamard matrix.
