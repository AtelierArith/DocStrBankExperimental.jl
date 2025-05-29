```
value_type(::Type{<:Union{AbstractModel,AbstractVariableRef}})
```

そのモデルの変数に対する[`value`](@ref)の戻り値の型を返します。実装されていない場合はデフォルトで`Float64`になります。

## 例

```jldoctest
julia> value_type(GenericModel{BigFloat})
BigFloat
```
