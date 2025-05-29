```
load_templates!(dir_templates::Union{String, Nothing} = nothing;
    remember_path::Bool = true,
    remove_templates::Bool = isnothing(dir_templates),
    store::Dict{Symbol, <:Any} = TEMPLATE_STORE,
    metadata_store::Vector{<:AITemplateMetadata} = TEMPLATE_METADATA)
```

パッケージのルートにあるフォルダ `templates/` からテンプレートを読み込み、`TEMPLATE_STORE` と `TEMPLATE_METADATA` に保存します。

注意: `remove_templates=true` の場合、`TEMPLATE_STORE` と `TEMPLATE_METADATA` から既存のテンプレートとメタデータを自動的に削除します。

# 引数

  * `dir_templates::Union{String, Nothing}`: テンプレートを読み込むためのディレクトリパス。`nothing` の場合、デフォルトのパスリストを使用します。通常、新しいテンプレートストレージを「登録」するために一度だけ使用されます。
  * `remember_path::Bool=true`: true の場合、将来のリフレッシュのためにパスを記憶します（`TEMPLATE_PATH` に）。
  * `remove_templates::Bool=isnothing(dir_templates)`: true の場合、`store` と `metadata_store` から既存のテンプレートとメタデータを削除します。
  * `store::Dict{Symbol, <:Any}=TEMPLATE_STORE`: テンプレートを読み込むためのストア。
  * `metadata_store::Vector{<:AITemplateMetadata}=TEMPLATE_METADATA`: メタデータを読み込むためのメタデータストア。

# 例

デフォルトのテンプレートを読み込む:

```julia
PT.load_templates!() # パスは必要ありません
```

新しいカスタムパスからテンプレートを読み込む:

```julia
PT.load_templates!("path/to/templates") # 将来のリフレッシュのためにこのパスを記憶します
```

デフォルトのテンプレートと新しいパスをリフレッシュしたい場合は、引数なしで `load_templates!()` を呼び出してください。
