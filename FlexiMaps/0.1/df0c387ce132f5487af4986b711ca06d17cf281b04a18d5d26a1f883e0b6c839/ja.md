```
mapset(X; prop=f, ...)
```

`X`のすべての要素`x`に対して`x.prop`の値を`f(x)`に設定します。一般的な使用法は、テーブルの列を変更することです。

`map(x -> @set(x.prop = f(x)), X)`と同等ですが、複数のプロパティをサポートします。

可能な場合（例えば`X isa StructArray`）：最適化されたアプローチを使用し、他のすべてのコンポーネントはそのまま保持します。
