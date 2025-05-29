```
codegen_ast_struct_head(def)
```

構造体のヘッダーを生成します。

# 例

```julia
julia> using Expronicon

julia> def = JLStruct(:(struct Foo{T} end))
struct Foo{T}
end

julia> codegen_ast_struct_head(def)
:(Foo{T})

julia> def = JLStruct(:(struct Foo{T} <: AbstractArray end))
struct Foo{T} <: AbstractArray
end

julia> codegen_ast_struct_head(def)
:(Foo{T} <: AbstractArray)
```
