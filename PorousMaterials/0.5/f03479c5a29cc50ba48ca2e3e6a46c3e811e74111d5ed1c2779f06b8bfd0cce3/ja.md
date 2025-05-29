```
total_ϕ = total_electrostatic_potential_energy(molecules, eparams, box, eikr)
```

配列の `Molecule` の総電気的ポテンシャルエネルギーをグランドカノニカルモンテカルロ（GCMC）アルゴリズムを使用して計算します。 #TODO これに追加する

# 引数

  * `molecules::Array{Molecule, 1}`: システムを構成する分子。
  * `eparams::EwaldParams`: エワルド和設定を含むデータ構造
  * `box::Box`: エネルギーが計算されるボックス。
  * `eikr::Eikr`: この計算に使用されるeikar、eikbr、およびeikcr OffsetArraysを格納します。

# 戻り値

  * `ϕ::GGEwaldSum`: 総電気的ポテンシャルエネルギー
