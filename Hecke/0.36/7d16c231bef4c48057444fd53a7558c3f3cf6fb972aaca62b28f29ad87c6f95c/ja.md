```
  is_subfield_normal(K::AbsSimpleNumField, L::AbsSimpleNumField) -> Bool, NumFieldHom{AbsSimpleNumField, AbsSimpleNumField}
```

$$
K
$$

が$L$の部分体である場合、`true`と$K$から$L$への注入を返します。そうでない場合、関数は`false`とすべてを`0`にマッピングする写像を返します。

この関数は$K$が正規であると仮定しています。
