```
SingleDofCost{Derivative,Class,Field,Tcost} <: AbstractElement
```

単一のノードを持つ要素で、指定されたdofにコストを追加します。  

# コンストラクタへの名前付き引数

  * `class::Symbol`、`:X`、`:U`、または`:A`のいずれか。
  * `field::Symbol`。
  * `cost::Function`、ここで 

      * `cost(x::ℝ,t::ℝ[,costargs...]) → ℝ` は `class` が `:X` または `:U` の場合、そして
      * `cost(x::ℝ,    [,costargs...]) → ℝ` は `class` が `:A` の場合。
  * `costargs::NTuple=()`
  * `derivative::Int=0` 0、1、または2 - どの時間微分がコストに入るか。

# リクエスト可能な内部変数

  * `cost`、コストの値。

# 例

```
using Muscade
model = Model(:TestModel)
node  = addnode!(model,𝕣[0,0])
e     = addelement!(model,SingleDofCost,[node];class=:X,field=:tx,
                    costargs=(3.,),cost=(x,t,three)->(x/three)^2)
```

参照: [`DofCost`](@ref)、[`ElementCost`](@ref)
