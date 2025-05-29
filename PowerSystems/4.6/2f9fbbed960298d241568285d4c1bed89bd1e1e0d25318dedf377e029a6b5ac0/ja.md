```julia
generate_struct_file(
    definition::InfrastructureSystems.StructDefinition;
    filename,
    output_directory
)

```

`StructDefinition`から1つの構造体のためのJuliaソースコードファイルを生成します。

利用可能なフィールドの説明については、`StructDefinition`および`StructField`を参照してください。

# 引数

  * `definition::StructDefinition`: 構造体とすべてのフィールドを定義します。
  * `filename::AbstractString`: このJSONファイルに構造体定義を追加します。デフォルトは`src/descriptors/power_system_structs.json`です。
  * `output_directory::AbstractString`: このディレクトリにファイルを生成します。デフォルトは`src/models/generated`です。
