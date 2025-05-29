```
generate_grid(celltype::Cell, nel::NTuple, [left::Vec, right::Vec)
```

1次元、2次元、または3次元の長方形のための`Grid`を返します。`celltype`はセルのタイプを定義します。例えば、`Triangle`や`Hexahedron`です。`nel`は各方向の要素数のタプルです。`left`と`right`はドメインのオプションの端点です。すべての方向でデフォルトは-1と1です。
