```
ZZLocalGenus
```

Local genus symbol over a p-adic ring.

The genus symbol of a component `p^m A` for odd prime `= p` is of the form `(m,n,d)`, where

  * `m` = valuation of the component
  * `n` = rank of A
  * `d = det(A) \in \{1,u\}` for a normalized quadratic non-residue `u`.

The genus symbol of a component `2^m A` is of the form `(m, n, s, d, o)`, where

  * `m` = valuation of the component
  * `n` = rank of `A`
  * `d` = `det(A)` in `{1,3,5,7}`
  * `s` = 0 (or 1) if even (or odd)
  * `o` = oddity of `A` (= 0 if s = 0) in `Z/8Z`     = the trace of the diagonalization of `A`

The genus symbol is a list of such symbols (ordered by `m`) for each of the Jordan blocks `A_1,...,A_t`.

Reference: [CS99](@cite) Chapter 15, Section 7.

# Arguments

  * `prime`: a prime number
  * `symbol`: the list of invariants for Jordan blocks `A_t,...,A_t` given as a list of lists of integers
