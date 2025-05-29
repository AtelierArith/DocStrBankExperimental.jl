```
reference_bonds(cryst::Crystal, max_dist)
```

距離 `max_dist` までの対称等価クラスごとに1つの結合の完全なリストを返します。各等価クラスの参照結合 `b` は、`basis_for_symmetry_allowed_couplings(cryst, b)` の要素の簡素化を優先するスコアリングシステムに従って選択されます。
