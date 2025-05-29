```julia
StructDefinition(
;
    struct_name,
    fields,
    supertype,
    docstring,
    is_component
)

```

コード自動生成の目的でStructDefinitionを構築します。

# 引数

  * `struct_name::AbstractString`: 構造体名
  * `fields::Vector{StructField}`: 構造体フィールド。[`StructField`](@ref)を参照してください。
  * `docstring::AbstractString`: 構造体のドキュメント文字列。デフォルトは空の文字列です。
  * `supertype::Union{String, DataType}`: 構造体のスーパタイプ。デフォルトではスーパタイプはありません。
  * `is_component::Bool`: システムに添付されるコンポーネントタイプの場合はtrueに設定します。デフォルトでtrueに設定しないでください。
