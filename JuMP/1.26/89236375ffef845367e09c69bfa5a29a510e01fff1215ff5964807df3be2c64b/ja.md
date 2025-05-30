```
SkipModelConvertScalarSetWrapper(set::MOI.AbstractScalarSet)
```

JuMPは[`model_convert`](@ref)を使用して、[`MOI.AbstractScalarSet`](@ref)セットをモデルと同じ[`value_type`](@ref)に自動的に昇格させます。

これが望ましくない場合は、セットを`SkipModelConvertScalarSetWrapper`でラップして、セットを変更せずにソルバーに渡します。

!!! warning
    この構造体はJuMP拡張によって内部で使用することを意図しています。通常のJuMPコードで使用する必要はありません。


## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> @constraint(model, x in MOI.EqualTo(1 // 2))
x = 0.5

julia> @constraint(model, x in SkipModelConvertScalarSetWrapper(MOI.EqualTo(1 // 2)))
x = 1//2
```
