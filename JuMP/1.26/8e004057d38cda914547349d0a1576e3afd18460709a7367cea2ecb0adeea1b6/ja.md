```
backend(model::GenericModel)
```

JuMPの下にある低レベルのMathOptInterfaceモデルを返します。このモデルは、JuMPがどの操作モードにあるかによって異なります（[`mode`](@ref)を参照）。

  * JuMPが`DIRECT`モードにある場合（つまり、モデルが[`direct_model`](@ref)を使用して作成された場合）、バックエンドは[`direct_model`](@ref)に渡されたオプティマイザになります。
  * JuMPが`MANUAL`または`AUTOMATIC`モードにある場合、バックエンドは`MOI.Utilities.CachingOptimizer`です。

バックエンドモデル内の変数または制約のインデックスを取得するには、[`index`](@ref)を使用してください。

!!! warning
    この関数は、低レベルのMathOptInterfaceまたはソルバー固有の機能にアクセスしようとする上級ユーザーのみが使用するべきです。


## 注意事項

JuMPが`DIRECT`モードでない場合、`backend`によって返される型は、任意のJuMPリリース間で変更される可能性があります。したがって、MathOptInterfaceによって公開されているAPIのみを使用し、内部フィールドにアクセスしないでください。最も内側のオプティマイザにアクセスする必要がある場合は、[`unsafe_backend`](@ref)を参照してください。あるいは、[`direct_model`](@ref)を使用して`DIRECT`モードのJuMPモデルを作成してください。

関連情報: [`unsafe_backend`](@ref)。

## 例

```jldoctest
julia> import HiGHS

julia> model = direct_model(HiGHS.Optimizer());

julia> set_silent(model)

julia> @variable(model, x >= 0)
x

julia> highs = backend(model)
A HiGHS model with 1 columns and 0 rows.

julia> index(x)
MOI.VariableIndex(1)
```
