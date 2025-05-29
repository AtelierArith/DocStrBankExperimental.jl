gg*energy = vdw*energy(molecule*id, molecules, ljforcefield, simulation*box)

単一の吸着物 `molecules[molecule_id]` とシステム内の他のすべての分子との間のファン・デル・ワールス相互作用エネルギーを計算します。最近接画像の規則を使用して周期境界条件が適用されます。

# 引数

  * `molecule_id::Int`: `molecules` 内のどの分子のゲスト-ゲスト相互作用を計算するかを決定するために使用される分子ID
  * `molecules::Array{Molecule, 1}`: 分子データ構造の配列
  * `ljforcefield::LJForceField`: 異なる原子間の相互作用を記述するレナード・ジョーンズ力場データ構造
  * `simulation_box::Box`: 計算のためのシミュレーションボックス。

# 戻り値

  * `gg_energy::Float64`: `molecules[molecule_id]` と `molecules` 内の他の分子との間のゲスト-ゲスト相互作用エネルギー
