```
copy_model(model::Model; filter_constraints::Union{Nothing, Function}=nothing)
```

モデル `model` のコピーと、与えられた `model` の参照に対応する新しいモデルの変数および制約の参照を取得するために使用できる [`ReferenceMap`](@ref) を返します。 [`Base.copy(::AbstractModel)`](@ref) メソッドも実装されており、これは `copy_model` に似ていますが、参照マップは返しません。

`filter_constraints` 引数が指定されている場合、この関数が `true` を返す制約のみがコピーされます。この関数には制約の参照が引数として渡されます。

## 注意

モデルのコピーは `DIRECT` モードではサポートされていません。つまり、[`Model`](@ref) コンストラクタの代わりに [`direct_model`](@ref) コンストラクタを使用してモデルが構築されるときです。さらに、モデル構築時にオプティマイザが提供されたかどうかに関係なく、新しいモデルにはオプティマイザがありません。つまり、[`optimize!`](@ref) 呼び出しで新しいモデルにオプティマイザを提供する必要があります。

## 例

以下の例では、変数 `x` と制約 `cref` を持つモデル `model` が構築されます。その後、新しい参照が `x_new` と `cref_new` に割り当てられたモデル `new_model` にコピーされます。

```julia
model = Model()
@variable(model, x)
@constraint(model, cref, x == 2)

new_model, reference_map = copy_model(model)
x_new = reference_map[x]
cref_new = reference_map[cref]
```
