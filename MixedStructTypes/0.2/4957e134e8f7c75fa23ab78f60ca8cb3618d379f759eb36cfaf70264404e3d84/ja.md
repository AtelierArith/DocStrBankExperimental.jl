```
@compact_structs(type_definition, structs_definitions)
```

このマクロは、複数の型を1つの型に結合することを可能にします。このバージョンは、単一の型を持つ場合とほぼ同じパフォーマンスを発揮するように設計されています。

## 例

```julia
julia> @compact_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> a = A(1)
A(1)::AB

julia> a.x
1
```
