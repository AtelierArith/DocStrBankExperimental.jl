```
unique_integer(x::AcbPolyRingElem)
```

定数多項式 $x$ に含まれるユニークな整数がある場合は、`true` を返すタプル `(t, z)` を返します。その整数 $z$ も含まれます。そうでない場合は、`t` を `false` に設定します。
