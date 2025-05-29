```
GoldenSample()
```

Generate a quasirandom Kronecker sequence using powers of the generalized golden ratio.

The harmonious, or generalized golden, ratios are defined as the solutions to the equation: $x^d = x + 1$

Where `d` is the dimension of the sequence. The Golden sequence is then equivalent to `Kronecker([x^-i for i in 1:d])`.

WARNING: the generalized golden sequence in more than 2 dimensions is purely experimental. It likely has poor discrepancy in high dimensions, and should not be used without verifying answers against a better-known quasirandom sequence. Try a rank-1 lattice rule instead.

References: Roberts, M. (2018). The Unreasonable Effectiveness of Quasirandom Sequences. *Extreme Learning.* http://extremelearning.com.au/unreasonable-effectiveness-of-quasirandom-sequences/
