```
tower_two_prime(bitsize::Integer, tower_len::Integer) -> BigInt
```

`bitsize` ビットの形 `2^towerlen * q + 1` のランダムな素数を返します。ここで `q` も素数です。

```
julia> tower_two_prime(22, 6)
2362433
```
