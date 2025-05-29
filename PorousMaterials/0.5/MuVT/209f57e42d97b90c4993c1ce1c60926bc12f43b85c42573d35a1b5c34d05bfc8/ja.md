```
results, molecules = μVT_sim(xtal, molecule_templates, temperature, pressure,
                             ljff; molecules=Array{Molecule, 1}[], settings=settings)
```

特定の温度と圧力でxtal内の分子の吸着をシミュレートするためのグランドカノニカル（μVT）モンテカルロシミュレーションを実行します。これはレナード・ジョーンズ力場を使用しています。

マルコフ連鎖モンテカルロの移動には以下が含まれます：

  * 削除/挿入
  * 平行移動
  * 再挿入
  * 同一性の変更（複数成分の場合） [こちらを参照](http://dx.doi.org/10.1080/00268978800100743)

平行移動のステップサイズは、バーニングサイクル中に動的に更新され、平行移動の受け入れ率は約0.4になります。

サイクルは、max(20, 現在システム内にある吸着物質の数)のマルコフ連鎖提案として定義されます。

# 引数

  * `xtal::Crystal`: 吸着をシミュレートしようとする多孔質のxtal
  * `molecule_templates::Array{Molecule, 1}`: シミュレートしようとするユニークな吸着分子のテンプレートの配列
  * `temperature::Float64`: 吸着相と平衡にあるバルクガス相の温度。単位: ケルビン (K)
  * `pressures::Array{Float64, 1}`: 吸着相と平衡にあるバルクガス相の圧力。単位: バール 吸着のための
  * `ljff::LJForceField`: 分子モデルを記述するために使用される
  * `molecules::Array{Array{Molecule{Cart}, 1}, 1}`: xtal内の分子の初期構成で、種ごとに配列があります。
  * `n_cycles_per_volume::Int`: ボリュームあたりのMCサイクルの数で、`n_burn_cycles`と`n_sample_cycles`の間で均等に分割されます。
  * `fraction_burn_cycles::Float64`: サンプリング前に燃焼するMCサイクルの割合
  * `sample_frequency::Int`: サンプリングサイクル中に、例えばこの数のマルコフ提案ごとに吸着されたガス分子の数をサンプリングします。
  * `verbose::Bool`: シミュレーション中に情報を印刷するかどうか
  * `ewald_precision::Float64`: ロングレンジEwald和のための望ましい精度
  * `eos::Symbol`: 圧力からフガシティを計算するために使用する状態方程式
  * `write_adsorbate_snapshots::Bool`: シミュレーションがスナップショットファイルを作成して保存するかどうか
  * `snapshot_frequency::Int`: 各スナップショットの間に取られるサイクルの数（バーニングサイクルの完了後）
  * `calculate_density_grid::Bool`: シミュレーションが吸着物質のための密度グリッドを追跡するかどうか
  * `density_grid_dx::Float64`: 密度グリッド内のボクセル間の（おおよその）スペース（オングストローム単位）。シミュレーションボックス内のボクセルの数は[`required_n_pts`](@ref)によって自動的に計算されます。
  * `density_grid_molecular_species::Symbol`: その位置（中心）の密度グリッドを作成する吸着物質。
  * `density_grid_sim_box::Bool`: 密度グリッドが渡された結晶のボックスではなく、シミュレーションボックス全体にわたることを望む場合は`true`。渡された元の`xtal.box`の上に密度グリッドを置くことを望む場合は`false`。
  * `autosave::Bool`: シミュレーション結果を標準のパス/ファイル名に自動的に保存したい場合は`true`。
  * `results_filename_comment::AbstractString`: 保存されたファイルの名前に追加されるオプションのコメント（自動保存された場合）
