```
cstatic"string"[N]
```

「string」から[`CStaticString`](@ref)を作成します。オプションで、コードユニットの数`N`を指定できます。

# 例

```jldoctest
julia> cstatic"Orada mısın"
cstatic"Orada mısın"13

julia> cstatic"Orada mısın"25
cstatic"Orada mısın"25

julia> ccall(:jl_printf, Cint, (Ptr{Nothing}, Ptr{Cchar},), stdout isa IOContext ? stdout.io : stdout, cstatic"Orada mısın\n"25)
Orada mısın
14
```
