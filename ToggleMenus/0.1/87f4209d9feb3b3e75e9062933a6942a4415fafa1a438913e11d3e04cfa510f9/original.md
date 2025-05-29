```
mutable struct ToggleMenu <: _ConfiguredMenu{Config}
    options::StringVector
    settings::Vector{Char}
    selections::Vector{Char}
    icons::Dict{Char,Union{String,Char}}
    header::Union{AbstractString,Function}
    braces::Tuple{String,String}
    maxicon::Int
    keypress::Function
    pagesize::Int
    pageoffset::Int
    cursor::Ref{Int}
    config::Config
    aux::Any
end
```
