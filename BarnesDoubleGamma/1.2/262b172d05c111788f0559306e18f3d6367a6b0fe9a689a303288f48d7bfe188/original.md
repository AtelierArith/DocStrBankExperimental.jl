```
log_barnesdoublegamma(z, τ)
```

Logarithm of Barne's G-function $\log(G(z; τ))$. Can get very expensive for high precision.

# Examples

```jldoctest
julia> z = 1; τ = sqrt(3); log_barnesdoublegamma(z, τ)
-3.5564013784958066e-9

julia> z = sqrt(big"2"); τ = sqrt(big"3"); log_barnesdoublegamma(z, τ)
0.293394920968626643183216869255154162603276275448888004730390602371621786480874
```
