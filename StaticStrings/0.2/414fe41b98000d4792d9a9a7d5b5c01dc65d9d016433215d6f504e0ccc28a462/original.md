```
cstatic"string"[N]
```

Create a [`CStaticString`](@ref) from "string". Optionally, specify the number of codeunits, `N`.

# Examples

```jldoctest
julia> cstatic"Orada mısın"
cstatic"Orada mısın"13

julia> cstatic"Orada mısın"25
cstatic"Orada mısın"25

julia> ccall(:jl_printf, Cint, (Ptr{Nothing}, Ptr{Cchar},), stdout isa IOContext ? stdout.io : stdout, cstatic"Orada mısın\n"25)
Orada mısın
14
```
