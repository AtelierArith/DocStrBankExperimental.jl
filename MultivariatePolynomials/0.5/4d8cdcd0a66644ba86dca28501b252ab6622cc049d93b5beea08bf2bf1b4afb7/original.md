```
struct GeneralizedEuclideanAlgorithm <: AbstractUnivariateGCDAlgorithm
    primitive_rem::Bool
    skip_last::Bool
end
```

Algorithm computing the greatest common divisor of univariate polynomials using the Euclidean algorithm generalized for polynomials with coefficients over a a unique factorization domain, see [Knu14, Algorithm E, p. 426-427].

If `primitive_rem` is `true`, the intermediate remainders produced in the polynomial division are made primitive. If `primitive_part` is set to `false`, only the resuting remainder is made primitive (the intermediate remainders of the generalized Euclidean algorithm still need to be made primitive).

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. Third edition.
