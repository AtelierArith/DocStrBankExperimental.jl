```
@sumtype SumTypeName(Types) [<: AbstractType]
```

このマクロは、指定された型から構成される合成型を作成します。オプションで抽象スーパタイプも受け入れます。

## 例

```julia
julia> using DynamicSumTypes

julia> struct A x::Int end;

julia> struct B end;

julia> @sumtype AB(A, B)
```
