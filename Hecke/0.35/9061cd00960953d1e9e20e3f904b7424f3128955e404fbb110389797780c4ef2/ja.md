```
is_subfield(K::SimpleNumField, L::SimpleNumField) -> Bool, Map
```

$$
K
$$

が$L$の部分体である場合、`true`と$K$から$L$への注入を返します。そうでない場合、関数は`false`とすべてを$0$にマッピングする写像を返します。
