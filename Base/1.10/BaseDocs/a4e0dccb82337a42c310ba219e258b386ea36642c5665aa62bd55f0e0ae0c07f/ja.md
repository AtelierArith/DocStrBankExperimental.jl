```
Union{Types...}
```

型のユニオンは、その引数型のいずれかのインスタンスをすべて含む抽象型です。空のユニオン [`Union{}`](@ref) は、Juliaの最下位型です。

# 例

```jldoctest
julia> IntOrString = Union{Int,AbstractString}
Union{Int64, AbstractString}

julia> 1 isa IntOrString
true

julia> "Hello!" isa IntOrString
true

julia> 1.0 isa IntOrString
false
```
