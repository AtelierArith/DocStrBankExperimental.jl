```
use_module_from_xml(xml_path::AbstractString, module_path::AbstractString)::Module
```

Use the module from the .jl files in the module_path and return a reference to this module. This reference can be passed into the load function.

# Examples

```julia-repl
julia> using XmlStructLoader
julia> module_ref = use_module_from_xml(path/to/xml/file.xml, path/to/module/module.jl)
```
