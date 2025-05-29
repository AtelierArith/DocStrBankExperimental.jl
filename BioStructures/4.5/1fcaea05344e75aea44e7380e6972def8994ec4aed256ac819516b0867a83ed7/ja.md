```
countatoms(el)
```

`StructuralElementOrList`内の原子の数を`Int`として返します。

追加の引数は原子セレクタ関数であり、すべての関数から`true`を返す原子のみがカウントされます。キーワード引数`expand_disordered`（デフォルトは`false`）は、無秩序な原子のすべてのコピーを別々に返すかどうかを決定します。
