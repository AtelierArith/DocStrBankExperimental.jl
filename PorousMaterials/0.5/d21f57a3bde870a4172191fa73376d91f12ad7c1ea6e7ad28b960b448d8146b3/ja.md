```
accessibility_grid, nb_segments_blocked, porosity = compute_accessibility_grid(crystal,
probe_molecule, ljforcefield; resolution::Union{Float64, Tuple{Int, Int, Int}}=1.0, energy_tol=10.0, energy_unit=:kJ_mol,
verbose=true, write_b4_after_grids=false, block_inaccessible_pockets=true)
```

単位セルに関する点のグリッドを重ねます。各点でプローブ分子のポテンシャルエネルギーを計算します。ポテンシャルエネルギーが `energy_tol` より小さい場合、そのグリッドポイントは吸着剤に対してアクセス可能と見なされます。そうでない場合はアクセス不可と見なされます。

`block_pockets` が true の場合: その後、グリッド内の異なる（接続されていない）セグメントにラベルを付けるためにフラッドフィルアルゴリズムを実行します。

次に、フラッドフィルされたグリッド内の接続されていないセグメントを頂点とし、周期境界を越えたセグメント間の接続をエッジとするグラフを構築します。

その後、グリッド内の単純なサイクルを見つけます。単純なサイクルに関与する頂点はアクセス可能と見なされます。なぜなら、分子はそのセグメントからホーム単位セルの同じセグメントに移動できるからです。サイクルに関与しない頂点がある場合、そのセグメントはアクセス不可と見なされ、このセグメント内のすべてのグリッドポイントはアクセス不可として再ラベル付けされます。

`accessibility_grid::Grid{Bool}` と `nb_segments_blocked` を返します。後者は、アクセス不可と判断されたためにブロックされたセグメントの数です。

# 引数

  * `crystal::Crystal`: アクセシビリティグリッドを計算するために求める結晶。
  * `probe_molecule::Molecule` プローブとして機能し、特定のポイントが占有可能かどうかを判断するための分子。
  * `LJForceField::LJForceField`: プローブ分子のポテンシャルエネルギーを計算するために使用されるフォースフィールド
  *   * `resolution::Union{Float64, Tuple{Int, Int, Int}}=1.0`: グリッドポイント間の最大距離（Å単位）または各次元のグリッドポイントの数を指定するタプル。
  * `energy_tol::Float64`: 計算されたポテンシャルエネルギーがこれより小さい場合、グリッドポイントは占有可能と見なされます。また、これはプローブ吸着剤がチャネル内の障壁を越えられないと仮定するエネルギー障壁です。単位は `energy_units` 引数によって与えられます。
  * `energy_units::Symbol`: 占有可能性の閾値を決定し、分子がチャネル内の障壁を越えられるかどうかを判断するために使用されるエネルギーの単位（`:kJ_mol` または `:K`）。（`energy_tol` を参照）
  * `write_b4_after_grids::Bool`: アクセシビリティの可視化のために、フラッドフィル/アクセス不可ポケットのブロックの前後で .cube ファイルを書き出します。
