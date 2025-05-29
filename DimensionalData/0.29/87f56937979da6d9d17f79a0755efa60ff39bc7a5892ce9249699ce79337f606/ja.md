```
rebuild(A::AbstractDimArray, data, [dims, refdims, name, metadata]) => AbstractDimArray
rebuild(A::AbstractDimArray; kw...) => AbstractDimArray
```

`AbstractDimArray`のフィールド変更を伴う再構築。`AbstractDimArray`を継承するすべての型は、追加のフィールドや異なるフィールド順序がある場合、このメソッドを定義しなければなりません。

実装では、`refdims`、`name`、`metadata`のような引数を無視することができます。

追加の引数はキーワード引数メソッドに追加できます。

可読性のために、引数が数個以上の場合はキーワードバージョンを使用することが望ましいです。
