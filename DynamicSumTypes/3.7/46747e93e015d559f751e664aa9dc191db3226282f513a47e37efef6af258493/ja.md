```
@sum_structs [version] type_definition begin
    structs_definitions
end
```

このマクロは、複数の型を1つの型に結合することを可能にします。デフォルトのバージョンは`:on_fields`で、これは単一の型を持つのとほぼ同じパフォーマンスを得るために構築されています。`:on_types`を使用すると、少し遅くなる代わりにメモリを少なく消費します。

## 例

```julia
julia> @sum_structs AB begin
           struct A x::Int end
           struct B y::Int end
       end

julia> a = AB'.A(1)
AB'.A(1)

julia> a.x
1
```
