```
apply_periodic_boundary_condition!(molecule::Molecule{Frac})
```

分子の重心座標が分数座標で (0.0, 1.0) の範囲内にあるかを確認し、必要に応じて変換します。

# 引数

  * `molecule::Molecule{Frac}`: チェックされる分子

# 戻り値

  * 分子が境界内にある場合は `nothing` を返します。それ以外の場合、入力された分子の座標が修正されます。
