```
is_const_prop_profitable_arg(𝕃::AbstractLattice, t) -> Bool
```

与えられた格要素 `t` が `𝕃` の新しい拡張格情報を持っているかどうかを判断し、それが定数伝播と共に転送されるべきであるかを判断します。
