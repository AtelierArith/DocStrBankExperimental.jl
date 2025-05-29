```
reverse_hash_position(hash::Integer, n::Integer, ::Val{N}) where N
```

`x`が`PeriodicVertex{N}`であるとき、`hash`が[`hash_position`](@ref)`(x, n)`から得られたものである場合、対応する`x`を返します。

返される`PeriodicVertex`のオフセットが必要ない場合、単に`mod1(x, n)`を行うことで頂点の識別子を得ることができ、より高速です。
