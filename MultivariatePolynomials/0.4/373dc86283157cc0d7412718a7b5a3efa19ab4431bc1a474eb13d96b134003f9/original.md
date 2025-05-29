```
function gcd(p1::AbstractPolynomialLike{T}, p2::AbstractPolynomialLike{S}) where {T, S}
```

Returns a greatest common divisor of `p1` and `p2`. Note that it does not make sense, in general, to speak of "the" greatest common divisor of u and v; there is a set of greatest common divisors, each one being a unit multiple of the others [Knu14, p. 424].

# Implementation notes

The classical algorithm for computing the `gcd`, commonly referred to as the Euclidean Algorithm is to use a recursion with the base case `gcd(p, 0) = p` and the relation `gcd(p1, p2) = gcd(p2, rem(p1, p2))`. The relation comes from the Euclidean division: `p1 = q * p2 + r`, if `g` divides `p1` and `p2` then it divides `r` and if `g` divides `r` and `p2` then it divides `p1`.

For multivariate polynomials, you may have `rem(p1, p2) = p1` hence this will not terminate. To ensure we make progress, we can pick a given variable `xi` and try to find `q1` and `q2` such that `q2 * p1 = q1 * p2 + r` and the degree of `r` in `xi` is strictly smaller than the degree of `p1` in `xi`. Note that if `g` divides `p1` and `p2` then it divides `r` but if `g` divides `r` and `p2` then it might divide `q2` and not `p1`. So what do we do ? Let `dj` be the degree of `pj` in `xi`. Suppose we pick `qj` to be the coefficient of `pj` in `xi^dj`. If `g` divides `q2` then it means that the degree of `g` in `xi` is zero. Therefore, if it divides `p2` then it also divides the coefficients of `p2` in `xi^k` for `k = 0, 1, ..., d2`. This means that if we ensure that these are relatively prime then we won't have any issue. So we start by computing a `gcd` `gj` of the coefficients in each degree of `xi` of `pj`, this is called the [`content`](@ref) of `pj`. And then we compute `_gcd(p1 / g1, p2 / g2) * gcd(g1, g2)` where we can use the recursion `_gcd(p1, p2) = _gcd(p2, q2 * p1 - q1 * p2)` where `q1, q2` are as defined above. This is the [`GeneralizedEuclideanAlgorithm`](@ref).

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. Third edition.
