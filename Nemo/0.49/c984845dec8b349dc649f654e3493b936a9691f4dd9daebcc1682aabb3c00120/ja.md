```
unique_integer(x::ArbPolyRingElem)
```

タプル `(t, z)` を返します。ここで、$t$ は `true` であれば $x$ の各係数に含まれるユニークな整数が存在することを示し、そうでなければ $t$ は `false` に設定されます。前者の場合、$z$ は整数多項式に設定されます。
