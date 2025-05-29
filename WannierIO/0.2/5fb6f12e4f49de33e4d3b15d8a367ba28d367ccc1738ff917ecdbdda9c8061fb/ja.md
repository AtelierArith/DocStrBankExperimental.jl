```julia
read_wout(filename; iterations)

```

wannier90 `wout` ファイルを解析します。

# キーワード引数

  * `iterations`: `true` の場合、すべての解離と最大局在の反復を解析します。デフォルトは `false` です。

# 返り値

  * `lattice`: 各列は Å の格子ベクトルです
  * `recip_lattice`: 各列は Å⁻¹ の逆格子ベクトルです
  * `atom_labels`: 原子記号
  * `atom_positions`: 分数座標で
  * `kgrid`: ワニエ化に使用される k点グリッド
  * `centers`: 各最終 WF の中心、Å 単位
  * `spreads`: 各最終 WF の広がり、Å² 単位
  * `sum_centers`: 最終 WF 中心の合計、Å 単位
  * `sum_spreads`: 最終 WF 広がりの合計、Å² 単位
  * `ΩI`, `ΩD`, `ΩOD`, `Ωtotal`: 最終広がり（成分）Å² 単位
  * `phase_factors`: オプション、実値（または実に近い）MLWF を得るためのグローバル（乗法的）位相因子
  * `im_re_ratios`: オプション、最大 Im/Re 比
  * `iterations`: 解離と最大局在の収束履歴、kwarg `iterations=true` の場合のみ解析されます。
