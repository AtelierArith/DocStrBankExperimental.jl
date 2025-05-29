```
DofLoad{Tvalue,Field} <: AbstractElement
```

単一のX-dofに荷重項を適用する要素です。  

# コンストラクタへの名前付き引数

  * `field::Symbol`。
  * `value::Function`、ここで `value(t::ℝ) → ℝ` です。

# リクエスト可能な内部変数

  * `F`、荷重の値。

# 例

```
using Muscade
model = Model(:TestModel)
node  = addnode!(model,𝕣[0,0])
e     = addelement!(model,DofLoad,[node];field=:tx,value=t->3t-1)
```

関連項目: [`Hold`](@ref), [`DofCost`](@ref)  
