```
safe_prime(bitsize::Integer) -> BigInt
```

`q = 2 * p + 1` の形を持つランダムな安全素数 `q` を返します。ここで `p` も素数です。返される素数は `bitsize` ビットを持ちます。

```
julia> safe_prime(10)
1439
```
