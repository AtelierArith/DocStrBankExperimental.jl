```
sqrt_mod_prime(a::Integer, p::Integer) -> Integer
```

`x^2 == a mod p` を解き、平方根の1つ `r` を返します。もう1つの根は `p - r` です。解がない場合は、例外をスローします。

```julia
julia> sqrt_mod_prime(33^2, 73)
33
```
