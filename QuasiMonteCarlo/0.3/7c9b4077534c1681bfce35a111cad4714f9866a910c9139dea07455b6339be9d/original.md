```
FaureSample(R::RandomizationMethod = NoRand()) <: DeterministicSamplingAlgorithm
```

A Faure low-discrepancy sequence.

Faure-distributed samples cover all dimensions evenly, using the same set of points for all variables, up to ordering.

When scrambled, randomized Faure sequences provide worst-case guarantees that variance will be at most `exp(1) ≈ 2.718` times greater than for a purely Monte Carlo integral. However, they are much less efficient than the Sobol sequence at integrating functions with low effective dimension (functions where the first few inputs dominate the evaluation).

The Faure sequence in dimension `s` forms a `(0, s)`-sequence with base `b = nextprime(s)`.

A Faure sequence must have length `k * base^s` with `k < base < 1`.

References: Faure, H. (1982). Discrépance de suites associées à un système de numération (en dimension s). *Acta Arith.*, 41, 337-351. Owen, A. B. (1997). Monte Carlo variance of scrambled net quadrature. *SIAM Journal on Numerical Analysis*, 34(5), 1884-1910.
