```
hasselection(x, selector) => Bool
hasselection(x, selectors::Tuple) => Bool
```

`x`に対して`selectors`でインデックスを付けることができるかを確認します。ここで、`x`は`dims`メソッドを持つオブジェクトであり、`selectors`は`Selector`または`Dimension`、またはそのいずれかのタプルです。
