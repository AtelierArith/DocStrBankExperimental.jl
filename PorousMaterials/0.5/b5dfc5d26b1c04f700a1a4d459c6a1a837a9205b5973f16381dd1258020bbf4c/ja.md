```
total_ϕ = total_electrostatic_potential_energy(crystal, molecules, eparams, eikr)
```

total*電気*ポテンシャルエネルギーの説明で、クリスタルを使用します

# 引数

  * `crystal::Crystal`: 結晶構造（電荷については `crystal.charges` を参照）
  * `molecules::Array{Molecule, 1}`: システムを構成する分子。
  * `eparams::EwaldParams`: エワルド和の設定を含むデータ構造
  * `eikr::Eikr`: この計算に使用されるeikar、eikbr、およびeikcrのOffsetArraysを格納します。
