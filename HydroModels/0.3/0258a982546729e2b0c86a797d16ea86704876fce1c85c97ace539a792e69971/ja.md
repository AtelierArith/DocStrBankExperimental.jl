```
HydroModel{N} <: AbstractModel
```

水のプロセスをシミュレーションするための複数のコンポーネントを統合した完全な水文学モデルを表します。

# フィールド

  * `components::Vector{<:AbstractComponent}`: 水文学計算コンポーネント（例: `HydroBucket`, `UnitHydrograph`）。
  * `infos::NamedTuple`: コンポーネントから集約された変数名（入力、出力、状態、パラメータ、nns）を含むメタデータ。
  * `_varindices::AbstractVector{AbstractVector{Int}}`: 各コンポーネントの入力変数インデックスで、データフローを管理するために構築中に自動的に決定されます。
  * `_outputindices::AbstractVector{Int}`: すべての内部変数から最終モデル出力を選択し、順序付けるために使用されるインデックス。

# コンストラクタ

```julia
HydroModel(; components::Vector{<:AbstractComponent}, name::Union{Symbol,Nothing}=nothing)
```

  * `components`: 必須。異なるモデルコンポーネントを含むベクター。
  * `name`: モデルを識別するためのオプションのシンボル。`nothing`の場合、一意の名前が生成されます。

# 使用例

```julia
# bucket1とrouting1が事前に定義されたAbstractComponentインスタンスであると仮定
model = HydroModel(
    name = :simple_catchment,
    components = [bucket1, routing1]
)

# モデルをシミュレート
# output = model(input_data, parameters)
```

# 注意事項

  * 型パラメータ `N` は、潜在的なディスパッチ最適化のために型レベルでモデル `name` をエンコードします。
  * コンポーネントの接続と変数のルーティング（`_varindices`, `_outputindices`）は自動的に処理されます。
  * 構築された `model` オブジェクトはシミュレーションを実行するために呼び出し可能です（詳細については関数呼び出し演算子のドキュメントを参照してください）。
