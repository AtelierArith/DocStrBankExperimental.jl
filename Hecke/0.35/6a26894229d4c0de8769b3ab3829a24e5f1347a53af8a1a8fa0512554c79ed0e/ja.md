```
is_isomorphic_with_map(K::AbsSimpleNumField, L::AbsSimpleNumField) -> Bool, NumFieldHom{AbsSimpleNumField, AbsSimpleNumField}
```

$$
K
$$

と$L$が同型であれば、`true`と$K$から$L$への同型を返します。そうでない場合、関数は"false"とすべてを0に写す写像を返します。
