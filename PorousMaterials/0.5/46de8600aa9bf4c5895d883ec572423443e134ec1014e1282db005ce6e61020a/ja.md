```
ϕ = electrostatic_potential_energy(crystal, molecule, eparams, eikr)
```

結晶内の分子の静電ポテンシャルエネルギーを計算します。

静電ポテンシャルは、`crystal.charges`に割り当てられた結晶原子の点電荷によって生成されます。周期境界条件はエワルド和を通じて適用されます。ここでは、モンテカルロシミュレーションにおけるエネルギーの*差*を見ているため、スプリアスな自己相互作用項は無視されています。

警告: `eparams.sr_cutoff_r`で供給された短距離カットオフ半径に対して最近接画像の規約が適用できるように、結晶が十分に複製されていると仮定されています。

# 引数

  * `crystal::Crystal`: 結晶構造（電荷については`crystal.charges`を参照）
  * `molecule::Molecule`: 結晶内の原子と比較される分子。
  * `eparams::EwaldParams`: エワルド和の設定を含むデータ構造
  * `eikr::Eikr`: この計算に使用されるeikar、eikbr、およびeikcrのOffsetArraysを格納します。

# 戻り値

  * `pot::EwaldSum`: `crystal`と`molecule`の間の静電ポテンシャル（単位: K）
