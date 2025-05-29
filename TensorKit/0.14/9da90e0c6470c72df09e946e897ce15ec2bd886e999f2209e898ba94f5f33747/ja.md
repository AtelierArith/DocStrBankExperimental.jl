```
supremum(V₁::ElementarySpace, V₂::ElementarySpace, V₃::ElementarySpace...)
```

複数の基本空間の上限を返します。すなわち、`V::ElementarySpace` のインスタンスであり、`V ≿ V₁`、`V ≿ V₂`、... かつこの性質を持つ他の `W ≺ V` は存在しません。これには、すべての引数が同じ値の `isdual( )` を持つ必要があり、返り値 `V` も同じ値を持ちます。
