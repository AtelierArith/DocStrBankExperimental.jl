```
print_symmetry_table(cryst::Crystal, max_dist)
```

すべてのサイトと結合の同値クラスに関する対称性情報を、最大結合距離 `max_dist` まで印刷します。これは、`reference_bonds(cryst, max_dist)` のすべての結合 `b` に対して `print_bond(cryst, b)` を呼び出すことと同等であり、`Bond(i, i, [0,0,0])` は単一のサイト `i` を指します。
