```
allvariants(SumType)
```

合計型に含まれるすべてのバリアント型を名前付きタプルで返します。

## 例

```julia
julia> using LightSumTypes

julia> struct A x::Int end;

julia> struct B end;

julia> @sumtype AB(A, B)

julia> allvariants(AB)
(A = A, B = B)
```
