```
pFq(α, β, z)
```

Compute the generalized hypergeometric function, defined by

$$
{}_pF_q(α, β, z) = \sum_{k=0}^\infty \dfrac{(\alpha_1)_k\cdots(\alpha_p)_k}{(\beta_1)_k\cdots(\beta_q)_k}\dfrac{z^k}{k!},
$$

where the series converges and elsewhere by analytic continuation.

External links: [DLMF](https://dlmf.nist.gov/16.2.1), [Wikipedia](https://en.wikipedia.org/wiki/Generalized_hypergeometric_function).

# Examples

```jldoctest
julia> pFq((), (), 0.1) # ≡ exp(0.1)
1.1051709180756477

julia> pFq((0.5, ), (), 1.0+0.001im) # ≡ exp(-0.5*log1p(-1.0-0.001im))
22.360679774997894 + 22.36067977499789im

julia> pFq((), (1.5, ), -π^2/4) # A root of a spherical Bessel function
4.042865030283967e-17

julia> pFq((), (1.5, ), -big(π)^2/4) # In extended precision
8.674364372518869408017614476652675180406967418943475242812160199356160822272727e-78

julia> pFq((1, ), (2, ), 0.01) # ≡ expm1(0.01)/0.01
1.0050167084168058

julia> pFq((1/3, ), (2/3, ), -1000) # A confluent hypergeometric with large argument
0.050558053946448855

julia> pFq((1, 2), (4, ), 1) # a well-poised ₂F₁
2.9999999999999996

julia> pFq((1, 2+im), (3.5, ), exp(im*π/3)) # ₂F₁ at that special point in ℂ
0.6786952632946592 + 0.4523504929285015im

julia> pFq((1, 2+im), (3.5, ), exp(im*big(π)/3)) # More digits, you say?
0.6786952632946589823300834090168381068073515492901393549193461972311801512528996 + 0.4523504929285013648194489713901658143893464679689810112119412310631860619947939im

julia> pFq((1, 2+im, 2.5), (3.5, 4), exp(im*π/3)) # ₃F₂ because why not
0.8434434031615691 + 0.34175507615463174im

julia> pFq((1, 2+im, 2.5), (3.5, 4), exp(im*big(π)/3)) # Also in extended precision
0.8434434031615690763389963048175253868863156451003855955719081209861492349268002 + 0.3417550761546319732614495656712509723030350666571102474299311122586948108413206im

julia> pFq((1, 1), (), -1) # A divergent series
0.5963473623231942

julia> pFq((1, 1), (), -big(1))
0.5963473623231940743410784993692793760741778601525487815734849104823272191142015
```
