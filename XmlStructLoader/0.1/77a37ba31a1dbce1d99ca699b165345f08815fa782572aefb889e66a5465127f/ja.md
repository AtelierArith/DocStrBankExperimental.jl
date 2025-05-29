```
load(xml_path::AbstractString, module_path::AbstractString; validate::Bool=true)
```

指定されたXMLファイルを、指定されたモジュールで定義された構造体に読み込み、読み込まれた構造体を返します。このモジュールはXsdToStruct.jlによって生成される必要があります。デフォルトでは、ローダーは指定されたXML内のデータがXSDで指定された制約に準拠しているかどうかを検証します。この検証をスキップするには、キーワード引数`validate`をfalseに設定できます。

# 例

```julia-repl
julia> using XmlStructLoader
julia> load(joinpath("path", "to", "xml", "file.xml"), joinpath("path", "to", "xsd", "module.jl"))
```
