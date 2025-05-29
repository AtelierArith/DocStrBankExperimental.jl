```
copy_conflict(model::Model)
```

モデル `model` の現在のコンフリクトのコピーと、与えられた `model` の参照に対応する新しいモデルの変数および制約の参照を取得するために使用できる [`ReferenceMap`](@ref) を返します。

これは、[`copy_model`](@ref) のためのフィルタリング関数を提供する便利な関数です。

## 注意

モデルのコピーは `DIRECT` モードではサポートされていません。つまり、[`Model`](@ref) コンストラクタの代わりに [`direct_model`](@ref) コンストラクタを使用してモデルが構築されるときです。さらに、モデル構築時にオプティマイザが提供されたかどうかに関係なく、新しいモデルにはオプティマイザがありません。つまり、[`optimize!`](@ref) 呼び出しで新しいモデルにオプティマイザを提供する必要があります。

## 例

以下の例では、変数 `x` と2つの制約 `cref` および `cref2` を持つモデル `model` が構築されます。このモデルには解がなく、2つの制約は相互に排他的です。ソルバーは [`compute_conflict!`](@ref) を使用してコンフリクトを計算するように求められます。次に、コンフリクトに参加している `model` の部分が `new_model` にコピーされます。

```julia
model = Model() # コンフリクトの洗練/IIS計算をサポートするソルバーを使用する必要があります。
# 例えば、CPLEXやGurobiなど
@variable(model, x)
@constraint(model, cref, x >= 2)
@constraint(model, cref2, x <= 1)

compute_conflict!(model)
if MOI.get(model, MOI.ConflictStatus()) != MOI.CONFLICT_FOUND
    error("不適合なモデルに対してコンフリクトを見つけることができませんでした。")
end

new_model, reference_map = copy_conflict(model)
```
