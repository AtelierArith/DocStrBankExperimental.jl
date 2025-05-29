```
tower_two_prime(bitsize::Integer, tower_len::Integer) -> BigInt
```

Return a random prime of the form `2^towerlen * q + 1` with `bitsize` bits and where `q` is also a prime.

```
julia> tower_two_prime(22, 6)
2362433
```
