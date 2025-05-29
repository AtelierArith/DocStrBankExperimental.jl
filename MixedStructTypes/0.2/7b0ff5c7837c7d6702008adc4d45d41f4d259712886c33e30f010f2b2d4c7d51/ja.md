```
@sum_structs(type_definition, structs_definitions)
```

このマクロは、複数の型を1つに結合することを可能にします。使用法は`@compact_structs`と同等ですが、このバージョンはメモリを少なく消費する代わりに遅くなります。

## 例

```julia
julia> @sum_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> a = A(1)
A(1)::AB

julia> a.x
1
```
