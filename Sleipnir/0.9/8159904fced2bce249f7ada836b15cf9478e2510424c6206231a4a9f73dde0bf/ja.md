ODINNでのシミュレーションのためのシミュレーションパラメータを保持する構造体。

```
struct SimulationParameters{I <: Integer, F <: AbstractFloat, VM <: VelocityMapping} <: AbstractParameters
```

# フィールド

  * `use_MB::Bool`: 質量バランスを使用するかどうかを示すフラグ。
  * `use_iceflow::Bool`: 氷の流れを使用するかどうかを示すフラグ。
  * `plots::Bool`: プロットを生成するかどうかを示すフラグ。
  * `velocities::Bool`: 速度を計算するかどうかを示すフラグ。
  * `overwrite_climate::Bool`: 気候データを上書きするかどうかを示すフラグ。
  * `use_glathida_data::Bool`: GLATHIDAデータを使用するかどうかを示すフラグ。
  * `tspan::Tuple{F, F}`: シミュレーションの時間範囲。
  * `step::F`: シミュレーションの時間ステップ。
  * `multiprocessing::Bool`: マルチプロセッシングを使用するかどうかを示すフラグ。
  * `workers::I`: マルチプロセッシングのためのワーカーの数。
  * `working_dir::String`: 作業ファイルのディレクトリ。
  * `test_mode::Bool`: テストモードで実行するかどうかを示すフラグ。
  * `rgi_paths::Dict{String, String}`: RGIパスの辞書。
  * `ice_thickness_source::String`: 氷の厚さデータのソース。
  * `mapping::VM`: 速度製品データキューブの座標から氷河グリッドへのデータをグリッド化するために使用するマッピング。
  * `gridScalingFactor::I`: テストを高速化するために使用されるグリッドのダウンサンプリング係数。デフォルト値は1で、ダウンサンプリングは適用されません。
