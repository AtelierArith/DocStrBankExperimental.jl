```
gamma_inc_minimax(a,x,z)
```

Compute $P(a,x)$ using minimax approximations given by:

$$
1/2 * \operatorname{erfc}(\sqrt{y}) - e^{-y}/\sqrt{2\pi a} ⋅ T(a,\lambda)
$$

where

$$
T(a,\lambda) = \sum_{0}^{N} c_{k}(z)a^{-k}
$$

This is a higher accuracy approximation of Temme expansion, which deals with the region near `a ≈ x` with `a` large. Refer Appendix F in the paper for the extensive set of coefficients calculated using Brent's multiple precision arithmetic (set at 50 digits) in [Brent (1978)](@cite brent_1978).

External links: [DLMF 8.12.8](https://dlmf.nist.gov/8.12.8)

See also: [`gamma_inc(a,x,ind)`](@ref SpecialFunctions.gamma_inc)
