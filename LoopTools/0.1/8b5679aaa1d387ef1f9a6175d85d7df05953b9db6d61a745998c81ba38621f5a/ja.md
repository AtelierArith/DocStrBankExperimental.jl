```
Dget(p1^2, p2^2, p3^2, p4^2, (p1+p2)^2, (p2+p3)^2, 
m1^2, m2^2, m3^2, m4^2; val_only = false)
```

すべての四点係数の有限部分を返します。詳細は[`dget`](@ref)を参照してください。

  * `val_only = false`の場合、`NamedTuple`を返します。それ以外の場合は`NTuple`を返します。
