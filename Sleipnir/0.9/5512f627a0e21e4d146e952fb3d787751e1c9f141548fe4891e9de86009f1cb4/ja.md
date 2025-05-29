`SimulationParameters`型のコンストラクタ、デフォルト値を含む。

```
SimulationParameters(;
    use_MB::Bool = true,
    use_iceflow::Bool = true,
    plots::Bool = true,
    velocities::Bool = true,
    overwrite_climate::Bool = false,
    use_glathida_data::Bool = false,
    tspan::Tuple{F, F} = (2010.0,2015.0),
    step::F = 1/12,
    multiprocessing::Bool = true,
    workers::I = 4,
    working_dir::String = "",
    test_mode::Bool = false,
    rgi_paths::Dict{String, String} = Dict{String, String}(),
    ice_thickness_source::String = "Farinotti19",
    mapping::VM = MeanDateVelocityMapping(),
    gridScalingFactor::I = 1,
) where {I <: Integer, F <: AbstractFloat, VM <: VelocityMapping}
```

# キーワード引数

  * `use_MB::Bool`: 質量収支を使用するかどうか（デフォルト: `true`）。
  * `use_iceflow::Bool`: 氷の流れを使用するかどうか（デフォルト: `true`）。
  * `plots::Bool`: プロットを生成するかどうか（デフォルト: `true`）。
  * `velocities::Bool`: 速度を計算するかどうか（デフォルト: `true`）。
  * `overwrite_climate::Bool`: 気候データを上書きするかどうか（デフォルト: `false`）。
  * `use_glathida_data::Bool`: GLATHIDAデータを使用するかどうか（デフォルト: `false`）。
  * `float_type::DataType`: 浮動小数点数のデータ型（デフォルト: `Float64`）。
  * `int_type::DataType`: 整数のデータ型（デフォルト: `Int64`）。
  * `tspan::Tuple{F, F}`: シミュレーションの時間範囲（デフォルト: `(2010.0, 2015.0)`）。
  * `step::F`: シミュレーションの時間ステップ（デフォルト: `1/12`）。
  * `multiprocessing::Bool`: マルチプロセッシングを使用するかどうか（デフォルト: `true`）。
  * `workers::I`: マルチプロセッシングのためのワーカー数（デフォルト: `4`）。
  * `working_dir::String`: シミュレーションの作業ディレクトリ（デフォルト: `""`）。
  * `test_mode::Bool`: テストモードで実行するかどうか（デフォルト: `false`）。
  * `rgi_paths::Dict{String, String}`: RGIパスの辞書（デフォルト: `Dict{String, String}()`）。
  * `ice_thickness_source::String`: 氷の厚さデータのソース、`"Millan22"`または`"Farinotti19"`のいずれか（デフォルト: `"Farinotti19"`）。
  * `mapping::VM`: 速度製品データキューブの座標から氷河グリッドへのデータをグリッド化するために使用するマッピング。
  * `gridScalingFactor::I`: グリッドのダウンサンプリング係数、テストのスピードアップに使用される。デフォルト値は1で、ダウンサンプリングは適用されない。

# 戻り値

  * `simulation_parameters`: 新しい`SimulationParameters`オブジェクト。

# 例外

  * `AssertionError`: `ice_thickness_source`が`"Millan22"`または`"Farinotti19"`でない場合。

# 注意事項

  * グローバル変数ODINN*OVERWRITE*MULTIがtrueに設定されている場合、マルチプロセッシングはどんな場合でも無効になります。これは、ドキュメント生成を修正するためであり、現時点ではLiterate.jlがマルチプロセッシングが有効な場合にフリーズします。
