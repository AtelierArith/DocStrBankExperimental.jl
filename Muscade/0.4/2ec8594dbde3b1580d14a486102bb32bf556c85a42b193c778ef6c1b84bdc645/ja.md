```
SingleUdof{XField,Ufield,Tcost} <: AbstractElement
```

これはUdofを作成し、その値にコストを関連付けます。Udofの値は、同じノード上のXdofに対して荷重として適用されます。

# コンストラクタへの名前付き引数

  * `Xfield::Symbol`。
  * `Ufield::Symbol`。
  * `cost::Function`、ここで `cost(x::ℝ,t::ℝ[,costargs...]) → ℝ` は `class` が `:X` または `:U` の場合、`cost(x::ℝ, [,costargs...]) → ℝ` は `class` が `:A` の場合です。
  * `costargs::NTuple`

# リクエスト可能な内部変数

  * `cost`、コストの値。

# 例

```
using Muscade
model = Model(:TestModel)
node  = addnode!(model,𝕣[0,0])
e     = addelement!(model,SingleUdofCost,[node];Xfield=:tx,Ufield=:utx,
                    costargs=(3.,),cost=(x,t,three)->(x/three)^2)
```

参照: [`DofCost`](@ref), [`ElementCost`](@ref)
