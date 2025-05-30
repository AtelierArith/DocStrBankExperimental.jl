```
GenericModel{T}([optimizer_factory]; kwargs...) where {T<:Real}
```

JuMPモデルの新しいインスタンスを作成します。

`optimizer_factory`が提供されている場合、モデルは`set_optimizer(model, optimizer_factory; kwargs...)`を使用してオプティマイザで初期化されます。`kwargs`の詳細については[`set_optimizer`](@ref)を参照してください。

`optimizer_factory`が提供されていない場合は、[`optimize!`](@ref)を呼び出す前に[`set_optimizer`](@ref)を使用してオプティマイザを設定してください。

## 値の型 `T`

値の型 `T` として `Float64` 以外の型を渡すことは高度な操作です。値の型は、選択したオプティマイザが期待するものと一致する必要があります。詳細についてはオプティマイザのドキュメントを参照してください。

文書化されていない場合、オプティマイザは `Float64` のみをサポートしていると仮定してください。

サポートされていない値の型を選択すると、[`MOI.UnsupportedConstraint`](@ref) または [`MOI.UnsupportedAttribute`](@ref) エラーが発生します。このエラーが発生するタイミング（モデルの構築中または[`optimize!`](@ref)の呼び出し中）は、ソルバーがJuMPにどのようにインターフェースされているかによります。

## 例

```jldoctest
julia> model = GenericModel{BigFloat}();

julia> typeof(model)
GenericModel{BigFloat}
```
