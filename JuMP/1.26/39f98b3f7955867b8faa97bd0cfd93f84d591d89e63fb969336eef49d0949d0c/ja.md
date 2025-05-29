```
optimizer_index(x::GenericVariableRef)::MOI.VariableIndex
optimizer_index(x::ConstraintRef{<:GenericModel})::MOI.ConstraintIndex
```

`x`に対応する変数または制約のインデックスを、関連するモデル`unsafe_backend(owner_model(x))`内で返します。

この関数は[`unsafe_backend`](@ref)と一緒に使用する必要があります。

より安全な代替手段として、[`backend`](@ref)と[`index`](@ref)を使用してください。詳細については、[`backend`](@ref)および[`unsafe_backend`](@ref)のドキュメントを参照してください。

## 例外

  * 最適化プログラムが設定されていない場合、[`NoOptimizer`](@ref)をスローします。
  * 最適化プログラムが設定されているが接続されていない場合、`ErrorException`をスローします。
  * インデックスがブリッジされている場合、`ErrorException`をスローします。

## 例

```jldoctest
julia> import HiGHS

julia> model = Model(HiGHS.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 0)
x

julia> MOI.Utilities.attach_optimizer(model)

julia> highs = unsafe_backend(model)
A HiGHS model with 1 columns and 0 rows.

julia> optimizer_index(x)
MOI.VariableIndex(1)
```
