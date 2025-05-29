```
Template(
    txt::String;
    path::Bool=true,
    config_path::String="",
    config::Dict{String, String} = Dict()
)
```

This is the only structure and function of this package. This structure has 4 parameter,

  * `txt` is the path to the template file or template of String type.
  * `path` determines whether the parameter `txt` represents the file path. The default value is `true`.
  * `config_path` is path to config file. The suffix of config file must be `toml`.
  * `config` is configuration of template. It is type of `Dict`, please see [configuraiton](#Configurations) for more detail.

# Rendering

After you create a Template, you just have to execute the codes! For this, you use the Function-like Object of Template structure.`tmp(; init::Dict{Symbol, T}) where {T}` variables are initialized by `init` Dict which contains the pair of name(String) and value. If you don't pass the `init`, the initialization won't be done.

# Example

This is a simple usage:

```julia-repl
julia> using OteraEngine
julia> txt = "Hello {{ usr }}!"
julia> tmp = Template(txt, path = false)
julia> init = Dict(:usr=>"OteraEngine")
julia> tmp(init = init)
```
