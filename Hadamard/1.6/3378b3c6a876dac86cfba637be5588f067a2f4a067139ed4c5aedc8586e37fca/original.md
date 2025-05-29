```
walsh(n)
```

Return a Walsh matrix of order `n`, which must be a power of two, in sequency ordering.  This is related to the Hadamard matrix [`hadamard(n)`](@ref) by a bit-reversal permutation followed by a Gray-code permutation of the rows.

Note that the linear operation `walsh(n) * x` can be computed much more efficiently, albeit in floating-point arithmetic, by `fwht(x) * n` (where the `* n` is due to the differing normalization, and can usually be eliminated by adjusting how you use the resulting vector) using the sequency-ordered fast Walsh–Hadamard transform function [`fwht`](@ref).
