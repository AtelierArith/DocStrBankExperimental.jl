```
mutable struct SubresultantAlgorithm <: AbstractUnivariateGCDAlgorithm
    skipped_divisions::Int
end
```

Algorithm computing the greatest common divisor of univariate polynomials using the Subresultant algorithm, see [Knu14, Algorithm C, p. 428-429].

The division by `g*h^δ` in the algorithm only works if the iteration of [Knu14, Algorithm R, p. 426] is carried out even when the divided polynomial has a zero term. For computational savings, we don't do that so we store in `skipped_division` the number of skipped divisions so that the division by `g*h^δ` can be adapted accordingly.

In [Knu14, Algorithm C, p. 426], it is stated that there should be ``

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. Third edition.
