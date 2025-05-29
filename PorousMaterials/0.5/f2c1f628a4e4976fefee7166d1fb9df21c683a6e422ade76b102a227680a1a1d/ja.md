energy = vdw_energy(crystal, molecule, ljforcefield)

分子と結晶の間のファン・デル・ワールス相互作用エネルギーを計算します。特定の原子の最も近い複製を見つけるために、最近接画像の規則を適用します。

警告: フレームワークが十分に複製されていると仮定されており、最近接画像の規則を適用できることが前提です。[`replicate`](@ref)および[`replication_factors`](@ref)を参照してください。
