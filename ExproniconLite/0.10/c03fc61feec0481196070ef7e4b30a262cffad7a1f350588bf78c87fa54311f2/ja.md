```
name_only(ex)
```

名前だけを残し、他のすべてを削除します。現在、関数呼び出し、型変数を持つ型、サブタイプ演算子 `<:`、および型注釈 `::` をサポートしています。

# 例

```julia
julia> using Expronicon

julia> name_only(:(sin(2)))
:sin

julia> name_only(:(Foo{Int}))
:Foo

julia> name_only(:(Foo{Int} <: Real))
:Foo

julia> name_only(:(x::Int))
:x
```
