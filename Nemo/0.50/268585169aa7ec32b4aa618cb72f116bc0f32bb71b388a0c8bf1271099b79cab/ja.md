```
is_prime(x::ZZRingElem)
is_prime(x::Int)
```

$ x $ が素数であれば `true` を返し、そうでなければ `false` を返します。

# 例

```jldoctest
julia> is_prime(ZZ(13))
true
```
