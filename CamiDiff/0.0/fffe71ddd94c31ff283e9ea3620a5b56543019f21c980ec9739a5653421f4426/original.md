```
fdiff_adams_moulton_expansion_coeff(k::Int; T=Int, msg=true)
fdiff_adams_moulton_expansion_polynom(k::Int; T=Int, msg=true)
```

Finite difference expansion coefficient vector $β ≡ [β_0(x),\ ⋯,\ β_k(x)]$. Note the *forward* vector ordering, which is the order of use in the summation below,

$$
-\frac{∇}{ln(1-∇)}
= \sum_{p=0}^{\infty}β_p∇^p
= 1 - \frac{1}{2}∇ - \frac{1}{12}∇^2 - \frac{1}{24}∇^3 +⋯.
$$

#### Examples:

```
julia> k = 5;
julia> β = fdiff_adams_moulton_expansion_polynom(k); println(β)
Rational{Int64}[1//1, -1//2, -1//12, -1//24, -19//720, -3//160]

julia> fdiff_adams_moulton_expansion_coeff(k)
-3//160

julia> D = denominator(gcd(β))
1440

julia> convert(Vector{Int},(β .* D)); println(o)
[1440, -720, -120, -60, -38, -27]

julia> k = 20;
julia> fdiff_adams_moulton_expansion_coeff(k)
Integer-overflow protection: output converted to BigInt
-12365722323469980029//4817145976189747200000
```
