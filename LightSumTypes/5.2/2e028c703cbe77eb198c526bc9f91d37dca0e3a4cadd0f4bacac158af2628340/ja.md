```
@sumtype SumTypeName(Types) [<: AbstractType]
```

指定された型で構成された合成型を作成します。オプションで抽象スーパタイプも受け入れます。

## 例

```julia
julia> using LightSumTypes

julia> struct A x::Int end;

julia> struct B end;

julia> @sumtype AB(A, B)
```
