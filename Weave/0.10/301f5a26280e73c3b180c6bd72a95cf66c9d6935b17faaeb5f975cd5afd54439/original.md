```
include_weave(source::AbstractString, informat::Union{Nothing,AbstractString} = nothing)
include_weave(m::Module, source::AbstractString, informat::Union{Nothing,AbstractString} = nothing)
```

Include code from Weave document calling `include_string` on all code from doc. Code is run in the path of the include document.
