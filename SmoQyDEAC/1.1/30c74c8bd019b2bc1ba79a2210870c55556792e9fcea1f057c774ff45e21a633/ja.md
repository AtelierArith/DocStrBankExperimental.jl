```
DEAC_Std(correlation_function::AbstractVector,
     correlation_function_error::AbstractVector,
     β::Float64,
     input_grid::Vector{Float64},
     out_ωs::Vector{Float64},
     kernel_type::String,
     num_bins::Int64,
     runs_per_bin::Int64,
     output_file::String,
     checkpoint_file::String;

     find_fitness_floor::Bool=true
     population_size::Int64=8,
     base_seed::Integer=8675309,
     number_of_generations::Int64=1000000,
     keep_bin_data=true,
     autoresume_from_checkpoint=false,
     verbose::Bool=false,
     
     fitness = 1.0,
     crossover_probability::Float64 = 0.9,
     self_adapting_crossover_probability::Float64 = 0.1,
     differential_weight::Float64 = 0.9,
     self_adapting_differential_weight_probability::Float64 = 0.1,
     self_adapting_differential_weight::Float64 = 0.9,
     user_mutation! = nothing 
     )

`correlation_function`で渡されたデータに対してDEACアルゴリズムを実行し、`correlation_function_error`で渡されたエラーから$\Chi^2$フィッティングを使用します。

# 引数

  * `correlation_function::AbstractVector`: τ/ωₙ空間の入力データ
  * `correlation_function_error::AbstractVector`: 入力データに関連するエラー
  * `β::Float64`: 逆温度
  * `input_grid::Vector{Float64}`: 0からβまでのτの均等に間隔を空けた値、端点を含むかωₙ
  * `out_ωs::Vector{Float64}`: AC出力用の均等に間隔を空けたエネルギー
  * `kernel_type::String`: 許可されるカーネルについては以下を参照
  * `num_bins::Int64`: 生成するビンの数
  * `runs_per_bin::Int64`: 統計のためのビンごとの実行回数
  * `output_file::String`: 出力辞書を保存するファイル。jld2形式を推奨
  * `checkpoint_file::String`: チェックポイントデータを保存するファイル。jld2形式を推奨

# オプション引数

  * `find_fitness_floor::Bool = false`: フィットネスの合理的なフロアを見つけ、その値をターゲットフィットネスに追加します。
  * `population_size::Int64 = 8`: DEACの個体数。6以上でなければなりません
  * `base_seed::Int64 = 8675309`: シード
  * `number_of_generations::Int64 = 100000`: 最大ミューテーションループ数
  * `keep_bin_data::Bool = true`: ビンデータを保存するかどうか
  * `autoresume_from_checkpoint::Bool = false`: 可能であればチェックポイントから再開します
  * `verbose::Bool = false`: 実行ごとの統計を印刷します
  * `fitness = 1.0`: χ²フィッティングのための単一の値または値の配列

# オプションアルゴリズム引数

  * `crossover_probability::Float64 = 0.9`: クロスオーバーの開始確率
  * `self_adapting_crossover_probability::Float64 = 0.1`: クロスオーバー確率が変化する可能性
  * `differential_weight::Float64 = 0.9`: 2番目および3番目の可変インデックスの重み
  * `self_adapting_differential_weight_probability::Float64 = 0.1`: SADが変化する可能性
  * `self_adapting_differential_weight::Float64 = 0.9`: SAD
  * `user_mutation! = nothing`: 各イテレーションに追加のミューテーションを加えるためのユーザー渡し関数。詳細については以下を参照

各実行は独自のシードを使用します。例えば、10ビンを100回の実行で実行する場合、シードは`base_seed:base_seed+999`を使用します。ベースシードを1000増やし、別の出力ファイル名を使用して、後でさらに統計を生成することができます。

# 出力

SmoQyDEACは、`output_file`引数を介して渡されたファイル名に辞書を保存します。同じ辞書が関数によって返されます。

# チェックポイント

SmoQyDEACは、`checkpoint_file`に渡されたパラメータに従って名前を付けたファイルを定期的に保存します。JLD2形式を推奨します。例えば、.jld2拡張子のファイルです。各ビンの完了後にこのファイルが保存されます。最後のビンが終了した後、このファイルは削除されます。`autoresume_from_checkpoint=true`の場合、SmoQyDEACはチェックポイントから再開しようとします。渡された引数がチェックポイントのものと一致しない場合、コードは終了します。
```
