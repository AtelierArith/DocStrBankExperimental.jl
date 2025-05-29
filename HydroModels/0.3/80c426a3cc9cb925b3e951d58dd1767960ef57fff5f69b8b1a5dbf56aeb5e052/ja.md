```
(model::HydroModel)(input::AbstractArray, params::ComponentVector; kwargs...)
```

提供された入力データとパラメータを使用して水文学モデルシミュレーションを実行します。

# 引数

  * `input::AbstractArray{T,D}`: 入力データ。形状は `(variables, timesteps)` (D=2, 単一ノード) または `(variables, nodes, timesteps)` (D=3, 複数ノード) です。
  * `params::ComponentVector`: コンポーネントの要件に従って構造化されたモデルパラメータ。

# キーワード引数

  * `initstates::ComponentVector`: 状態を持つコンポーネントのためのオプションの初期状態。コンポーネント定義のデフォルトにデフォルト設定されます。
  * `config::Union{NamedTuple, Vector{<:NamedTuple}}`: コンポーネントのためのオプションの設定 (例: ODEソルバー、補間)。すべてに適用される単一の `NamedTuple` またはコンポーネント固有の設定のための `Vector` であることができます。
  * `kwargs...`: 該当する場合、個々のコンポーネントに渡される他のキーワード引数。

# 戻り値

  * `AbstractArray`: モデル出力で、形状は入力の時間 (およびノード、D=3の場合) 次元に一致します: `(output_variables, timesteps)` または `(output_variables, nodes, timesteps)`。

# 例

```julia
# 'model' が構築された HydroModel インスタンスであると仮定
# input_data は行列または3D配列である可能性があります
# parameters は ComponentVector です
output = model(input_data, parameters; initstates=initial_conditions)
```

# 注意事項

  * この関数は、モデルのコンポーネントを通じてデータフローを順次調整します。
  * 入力変数の次元 (`size(input, 1)`) は `get_input_names(model)` と一致する必要があります。
  * 状態の進化と出力の収集は内部で処理されます。
