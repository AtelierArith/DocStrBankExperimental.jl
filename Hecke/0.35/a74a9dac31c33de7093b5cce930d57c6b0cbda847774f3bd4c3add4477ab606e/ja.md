```
is_power(a::AbsSimpleNumFieldElem, n::Int; with_roots_unity::Bool = false) -> Bool, AbsSimpleNumFieldElem
```

$$
a
$$

が$n$-乗根を持つかどうかを判断します。これが真である場合、根が返されます。

体$K$が$n$-乗根を含むことが知られている場合、`with_roots_unity`を`true`に設定できます。
