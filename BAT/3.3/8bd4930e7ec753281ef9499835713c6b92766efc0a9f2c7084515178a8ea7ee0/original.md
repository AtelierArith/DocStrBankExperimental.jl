```
struct SokalAutocorLen <: AutocorLenAlgorithm
```

Integrated autocorrelation length estimation based on the automated windowing procedure descibed in [A. D. Sokal, "Monte Carlo Methods in Statistical Mechanics" (1996)](https://www.semanticscholar.org/paper/Monte-Carlo-Methods-in-Statistical-Mechanics%3A-and-Sokal/0bfe9e3db30605fe2d4d26e1a288a5e2997e7225)

Same procedure is used by the emcee Python package (v3.0).

Constructors:

  * `SokalAutocorLen(; fields...)`

Fields:

  * `c::Int64`: Step size for window search Default: 5
