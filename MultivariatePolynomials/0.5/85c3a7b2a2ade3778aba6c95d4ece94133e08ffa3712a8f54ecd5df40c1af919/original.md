```
pseudo_divrem(f::_APL{S}, g::_APL{T}, algo) where {S,T}
```

Return the pseudo divisor and remainder of `f` modulo `g` as defined in [Knu14, Algorithm R, p. 425].

When the coefficient type is not a field, it is not always possible to carry a division. For instance, the division of `f = 3x + 1` by `g = 2x + 1` cannot be done over integers. On the other hand, one can write `2f = 3g - 1`. In general, the *pseudo* division of `f` by `g` is:

$$
l f(x) = q(x) g(x) + r(x)
$$

where `l` is a power of the leading coefficient of `g` some constant.

See also [`pseudo_rem`](@ref).

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. Third edition.
