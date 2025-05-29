```
forcefield_coverage(atoms, ljforcefield)
forcefield_coverage(molecule, ljforcefield)
forcefield_coverage(crystal, ljforcefield)
```

`atoms::Atoms`内のすべての`species`に対してパラメータが含まれているか確認します。欠けている原子を出力します。

# 引数

  * `atoms::Atoms`: 原子のセット
  * `ljforcefield::LJForceField`: 原子相互作用に関する情報を含むレナード・ジョーンズ力場オブジェクト

# 戻り値

  * `all_covered::Bool`: 原子内のすべての種が力場でカバーされている場合はtrueを返します。
