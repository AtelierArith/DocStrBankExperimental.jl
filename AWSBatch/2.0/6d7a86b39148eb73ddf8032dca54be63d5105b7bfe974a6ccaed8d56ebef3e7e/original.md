```
register(
    definition_name::AbstractString;
    role::AbstractString="",
    image::AbstractString="",
    vcpus::Integer=1,
    memory::Integer=1024,
    cmd::Cmd=``,
    region::AbstractString="",
    parameters::Dict{String,String}=Dict{String, String}(),
) -> JobDefinition
```

Registers a new job definition.
