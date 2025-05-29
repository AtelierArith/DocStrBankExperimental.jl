```
rebuild(A::AbstractDimArray, data, [dims, refdims, name, metadata]) => AbstractDimArray
rebuild(A::AbstractDimArray; kw...) => AbstractDimArray
```

`AbstractDimArray`を再構築し、いくつかのフィールドを変更します。`AbstractDimArray`から継承するすべての型は、追加のフィールドや異なるフィールド順序がある場合、このメソッドを定義する必要があります。

実装では、`refdims`、`name`、`metadata`のような引数を破棄することができます。

追加の引数はキーワード引数メソッドに追加できます。

可読性のために、引数が数個以上ある場合はキーワードバージョンを使用することが望ましいです。
