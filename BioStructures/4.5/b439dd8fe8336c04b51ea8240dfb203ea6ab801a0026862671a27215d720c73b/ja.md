```
coordarray(element, atom_selectors...)
```

`StructuralElementOrList`の原子座標をÅ単位で2D `Array`として取得します。

各列は1つの原子に対応するため、サイズは(3, n*atoms)です。追加の引数は原子セレクタ関数であり、すべての関数から`true`を返す原子のみが保持されます。キーワード引数`expand*disordered`（デフォルトは`false`）は、無秩序原子のすべてのコピーの座標を個別に返すかどうかを決定します。
