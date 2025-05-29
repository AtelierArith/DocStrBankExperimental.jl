```
strRational(n::T) where T<:Union{Rational{}, Int, BigInt}
```

Fraction notation for rational numbers and integers

#### Examples:

```
julia> strRational(-5//2)
"-5/2"
```
