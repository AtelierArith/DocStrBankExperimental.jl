```
is_quadratic_residue(a::Integer, p::Integer) -> Bool
```

`a`が`p`の二次剰余であるかどうかに応じて、真または偽を返します。

つまり、`x^2 == a mod p`に解があるかどうかをチェックします。
