```
molecule = ion(q, coords)
```

点電荷を構築するために分子を構築します: Molecule(:ion, Atoms{Frac}(0), Charges(q, coords), coords)

# 引数

  * `q::Float64`: 点電荷の値、単位: 電子
  * `coords::Frac`: 電荷の分数座標

# 戻り値

  * `molecule::Molecule{Frac}`: 分数座標を持つ分子としてのイオン
