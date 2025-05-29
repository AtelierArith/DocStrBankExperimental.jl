```
isequal_canonical(
    aff::GenericAffExpr{C,V},
    other::GenericAffExpr{C,V}
) where {C,V}
```

`aff`がゼロを無視し、順序を考慮せずに`other`と等しい場合は`true`を返します。主にテストに便利です。
