```
protojl(
    relative_paths::Union{String,Vector{String}},
    search_directories::Union{String,Vector{String},Nothing}=nothing,
    output_directory::Union{String,Nothing}=nothing;
    include_vendored_wellknown_types::Bool=true,
    always_use_modules::Bool=true,
    force_required::Union{Nothing,Dict{String,Set{String}}}=nothing,
    add_kwarg_constructors::Bool=false,
    parametrize_oneofs::Bool=false,
    common_abstract_type::Bool=false,
) -> Nothing
```

Generate Julia code for `.proto` files at `relative_paths` within `search_directories` and save it to `output_directory`.

When compiling a `{file_name}.proto` files that do not have a `package` specifier, a `{file_name}_pb.jl` is generated in `output_directory`. When a `{file_name}.proto` contains e.g. `package foo_bar.baz_grok`, the following directory structure is created:

```bash
root  # `output_directory` arg from from `protojl`
└── foo_bar
    ├── foo_bar.jl  # defines module `foo_bar`, imports `baz_grok`
    └── baz_grok
        ├── {file_name}_pb.jl
        └── baz_grok.jl  # defines module `baz_grok`, includes `{file_name}_pb.jl`
```

You should include the top-level module of a generated package, i.e. `foo_bar.jl` in this example. All imported `.proto` files are compiled as well; an error is thrown if they cannot be resolved or found within `search_directories`.

# Arguments

  * `relative_paths::Union{String,Vector{String}}`: A path or paths to `.proto` files to be compiled.
  * `search_directories::Union{String,Vector{String},Nothing}=nothing`: A directory or directories to search for `relative_paths` in. By default, the current directory is used.
  * `output_directory::Union{String,Nothing}=nothing`: Path to store the generated Julia source code. When omitted, the translated code is saved to temp directory, the path is shown as a @info log.

# Keywords

  * `include_vendored_wellknown_types::Bool=true`: Append `ProtoBuf.VENDORED_WELLKNOWN_TYPES_PARENT_PATH` to `search_directories`, making the "well-known" message definitions available.
  * `always_use_modules::Bool=true`: Generate julia code in a module even if the `.proto` file doesn't contain a `package` specifier. The module name of `{file_name}.proto` file is `{file_name}_pb`.
  * `force_required::Union{Nothing,Dict{String,Set{String}}}=nothing`: Assume `message` and `oneof` fields to be aleways send over the wire – then we woudln't need to `Union` their respective types with `Nothing`. E.g:

```julia
# force_required === nothing
struct MyMessage
    message_field::Union{Nothing,MyOtherMessage}}
end
```

```julia
# force_required === Dict("{file_name}.proto" => Set(["MyMessage.message_field"]))
struct MyMessage
    message_field::MyOtherMessage}
end
```

  * `add_kwarg_constructors::Bool=false`: For each message, generate an outer constructor with optional keyword arguments (if a field is a required message, there are no default values and the keyword argument is not optional).
  * `parametrize_oneofs::Bool=false`: Add the `OneOf` type as a type parameter to the generated parent struct. I.e. this changes:

```julia
# parametrize_oneofs == false
struct MyMessage
    oneof_field::Union{Nothing, OneOf{<:Union{Int, String}}}
end
```

to

```julia
# parametrize_oneofs == true
struct MyMessage{T1<:Union{Nothing, OneOf{<:Union{Int, String}}}}
    oneof_field::T1
end
- `common_abstract_type::Bool=false`: When `true`, all generated structs will subtype `ProtoBuf.AbstractProtoBufMessage`.
```

# Notes

We use `relative_paths` and `search_directories` instead of absolute paths to resolve proto `import` statements which are using relative paths.
