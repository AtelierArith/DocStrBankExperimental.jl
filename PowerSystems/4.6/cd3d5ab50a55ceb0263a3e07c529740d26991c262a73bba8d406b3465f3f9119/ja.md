```julia
generate_struct_files(
    definitions;
    filename,
    output_directory
)

```

複数の `StructDefinition` インスタンスのイテラブルから構造体のJuliaソースコードファイルを生成します。

利用可能なフィールドの説明については `StructDefinition` と `StructField` を参照してください。

# 引数

  * `definitions`: 構造体とすべてのフィールドを定義します。
  * `filename::AbstractString`: このJSONファイルに構造体定義を追加します。デフォルトは `src/descriptors/power_system_structs.json`
  * `output_directory::AbstractString`: このディレクトリにファイルを生成します。デフォルトは `src/models/generated`
