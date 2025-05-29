```
strRational(n::T) where T<:Union{Rational{}, Int, BigInt}
```

有理数と整数の分数表記

#### 例:

```
julia> strRational(-5//2)
"-5/2"
```
