```
is_generator(g::Integer, q::Integer, factors::Array) -> Bool
```

Returns true if `g` is a generator of `Z_q` where `q` is prime and `factors` is the prime factorization of `q - 1 = p1^e1 * p2^e2 ... * pk^ek`.

```
q = 2^7 * 5 + 1
is_generator(2, q, [2, 5]) -> false
is_generator(3, q, [2, 5]) -> true
```
