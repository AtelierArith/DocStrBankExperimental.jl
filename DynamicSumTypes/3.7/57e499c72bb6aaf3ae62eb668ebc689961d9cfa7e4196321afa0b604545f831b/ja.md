```
variant(inst)
```

合計型に囲まれたバリアントを返します。

## 例

```julia
julia> using DynamicSumTypes

julia> struct A x::Int end;

julia> struct B end;

julia> @sumtype AB(A, B)

julia> a = AB(A(0))
AB'.A(0)

julia> variant(a)
A(0)
```
