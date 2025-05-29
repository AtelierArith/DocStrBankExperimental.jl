```
ϕ = electrostatic_potential_energy(molecules, eparams, box, eikr)
```

分子の配列から構成されるシステムの静電ポテンシャルエネルギーを計算します。

ここではEWald和が二重forループで使用されます。この関数は計算コストが高いため、モンテカルロシミュレーションには使用しないでください。

Ewald和の短距離および長距離の寄与、ならびに虚偽の自己相互作用および分子内相互作用を含む`EwaldSum`型を返します。アクセスは(ϕ.sr, ϕ.lr, ϕ.self, ϕ.intra)を介して行います。

エネルギーの単位: ケルビン

# 引数

  * `molecules::Array{Molecules, 1}`: システムを構成する分子の配列。
  * `eparams::EwaldParams`: Ewald和の設定を含むデータ構造
  * `box::Box`: エネルギーが計算されるボックス
  * `eikr::Eikr`: この計算に使用されるeikar、eikbr、およびeikcrのOffsetArraysを格納します。

# 戻り値

  * `ϕ::GGEwaldSum`: 総静電ポテンシャルエネルギー
