```
univariate_gcd(p1::AbstractPolynomialLike, p2::AbstractPolynomialLike, algo::AbstractUnivariateGCDAlgorithm)
```

Return the *greatest common divisor* of the polynomials `p1` and `p2` that have at most one variable in common and for which the coefficients are either `AbstractFloat` or part of a unique factorization domain, e.g., rational numbers, integers or multivariate polynomials. So `p1` and `p2` should have at most one variable in common but their coefficients can be multivariate polynomials that share arbitrarily many variables.

If the coefficients are not `AbstractFloat`, this

1. separates `p1` and `p2` in their [`content`](@ref) and [`primitive_part`](@ref) using [`primitive_part_content`](@ref); see [Knu14, Algorithm E: E1, p. 426] or [Knu14, Algorithm C: C1, p. 428].
2. Computes the [`gcd`](@ref) of the contents and primitive parts, using [`primitive_univariate_gcd!`](@ref) for primitive parts.
3. Return the product of these two `gcd`; see [Knu14, Algorithm E: E4, p. 427] or [Knu14, Algorithm C: C4, p. 429].

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. Third edition.
