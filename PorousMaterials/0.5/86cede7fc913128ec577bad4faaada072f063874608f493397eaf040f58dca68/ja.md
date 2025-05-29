```
random_reinsertion!(molecule, box)
```

分子に対して直交座標系での平行移動の摂動を行い、周期境界条件を適用し、元の分子のコピーを保持して、必要に応じて復元できるようにします。

# 引数

  * `molecule::Molecule{Frac}`: 移動させる分子
  * `box::Box`: 回転に使用されるボックス

# 戻り値

  * `old_molecule::Molecule{Frac}`: 元の分子のコピー
