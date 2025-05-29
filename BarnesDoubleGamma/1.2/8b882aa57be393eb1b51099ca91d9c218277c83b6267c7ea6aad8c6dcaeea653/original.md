```
barnesdoublegamma(z, τ)
```

Barne's G-function $G(z, τ)$. Can get very expensive for high precision.

# Examples

```jldoctest
julia> z = big"1"; τ = sqrt(big"3"); barnesdoublegamma(z, τ)
0.9999999999999999999999999999999999999999999999265240691883395187060685710095162

julia> z = sqrt(big"2"); τ = sqrt(big"3"); barnesdoublegamma(z, τ)
1.340972263940081256497568500074283394055091822104168575112011391955491855627026

julia> z = big(sqrt(3)); τ = sqrt(big"3"); barnesdoublegamma(z, τ)
1.488928335365086422942328604671778776079655676458875630387076246079377268516627
```
