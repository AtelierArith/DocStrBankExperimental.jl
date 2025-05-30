```
copy_conflict(model::GenericModel)
```

モデル `model` の現在のコンフリクトのコピーと、与えられた `model` の参照に対応する新しいモデルの変数および制約の参照を取得するために使用できる [`GenericReferenceMap`](@ref) を返します。

これは、[`copy_model`](@ref) のためのフィルタリング関数を提供する便利な関数です。

## 注意

モデルのコピーは `DIRECT` モードではサポートされていません。つまり、[`Model`](@ref) コンストラクタの代わりに [`direct_model`](@ref) コンストラクタを使用してモデルが構築される場合です。さらに、モデル構築時にオプティマイザが提供されたかどうかに関係なく、新しいモデルにはオプティマイザがありません。つまり、[`optimize!`](@ref) 呼び出しで新しいモデルにオプティマイザを提供する必要があります。

## 例

以下の例では、変数 `x` と2つの制約 `c1` および `c2` を持つモデル `model` が構築されます。このモデルには解がなく、2つの制約は相互に排他的です。ソルバーは [`compute_conflict!`](@ref) を使用してコンフリクトを計算するように求められます。コンフリクトに参加している `model` の部分は、モデル `iis_model` にコピーされます。

```julia
julia> using JuMP

julia> import Gurobi

julia> model = Model(Gurobi.Optimizer);

julia> set_silent(model)

julia> @variable(model, x >= 0)
x

julia> @constraint(model, c1, x >= 2)
c1 : x ≥ 2

julia> @constraint(model, c2, x <= 1)
c2 : x ≤ 1

julia> optimize!(model)

julia> compute_conflict!(model)

julia> if get_attribute(model, MOI.ConflictStatus()) == MOI.CONFLICT_FOUND
           iis_model, reference_map = copy_conflict(model)
           print(iis_model)
       end
Feasibility
Subject to
 c1 : x ≥ 2
 c2 : x ≤ 1
```
