```
import_module_from_xml(xml_path::AbstractString, module_path::AbstractString)::Module
```

module_path内の.jlファイルからモジュールをインポートし、このモジュールへの参照を返します。この参照はload関数に渡すことができます。

# 例

```julia-repl
julia> using XmlStructLoader
julia> module_ref = import_module_from_xml(path/to/xml/file.xml, path/to/module/module.jl)
```
