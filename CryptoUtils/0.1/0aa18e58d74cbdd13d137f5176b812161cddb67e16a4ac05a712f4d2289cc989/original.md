```
safe_prime(bitsize::Integer) -> BigInt
```

Return a random safe-prime `q` of the form `q = 2 * p + 1` where `p` is also a prime number. The returning prime number has `bitsize` bits.

```
julia> safe_prime(10)
1439
```
