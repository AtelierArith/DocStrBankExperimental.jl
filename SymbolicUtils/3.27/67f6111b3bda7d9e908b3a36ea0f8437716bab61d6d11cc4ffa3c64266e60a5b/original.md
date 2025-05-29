```
flatten_fractions(x)
```

Flatten nested fractions that are added together.

```julia
julia> flatten_fractions((1+(1+1/a)/a)/a)
(1 + a + a^2) / (a^3)
```
