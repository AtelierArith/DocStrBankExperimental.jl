```
KroneckerSample(generator::AbstractVector, R::RandomizationMethod = NoRand()) <: DeterministicSamplingAlgorithm
```

A Kronecker sequence is a point set generated using a vector and equation: `x[i] = i * generator .% 1`

Where `i` runs from `1` through the sample size `n`. This sequence will be equidistributed (uniform in the infinite limit) so long as the components of `generator` are linearly independent over the field of rational numbers.

If no generator is specified, a lattice based on the generalized golden ratio is used; see `GoldenSample` for more information.

Kronecker sequences are not recommended for use in more than 3 dimensions, as theory on them is sparse. `LatticeRuleSample` will return rank-1 lattice rules, which behave similarly to Kronecker sequences but have better properties.

References: Leobacher, G., & Pillichshammer, F. (2014). *Introduction to quasi-Monte Carlo integration and applications.* Switzerland: Springer International Publishing. https://link.springer.com/content/pdf/10.1007/978-3-319-03425-6.pdf
