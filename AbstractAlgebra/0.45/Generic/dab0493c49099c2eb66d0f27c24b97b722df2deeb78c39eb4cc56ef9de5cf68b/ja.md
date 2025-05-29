```
getindex(xi::SkewDiagram, n::Integer)
```

`n`が`xi.mu`に含まれていない`xi.lam`の（列優先）エントリに対応する場合は`1`を返します。それ以外の場合は`0`を返します。
