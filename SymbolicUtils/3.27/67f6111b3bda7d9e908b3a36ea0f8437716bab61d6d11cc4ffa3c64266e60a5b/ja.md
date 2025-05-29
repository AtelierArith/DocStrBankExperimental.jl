```
flatten_fractions(x)
```

加算されたネストされた分数をフラットにします。

```julia
julia> flatten_fractions((1+(1+1/a)/a)/a)
(1 + a + a^2) / (a^3)
```
