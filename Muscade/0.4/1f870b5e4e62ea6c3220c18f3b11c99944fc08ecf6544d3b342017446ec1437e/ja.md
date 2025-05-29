```
Hold <: AbstractElement
```

単一のX-dofをゼロに設定する要素です。  

# コンストラクタへの名前付き引数

  * `field::Symbol`。制約をかけるX-dofのフィールド。
  * `λfield::Symbol=Symbol(:λ,field)`。ラグランジュ乗数のフィールド。

# 例

```
using Muscade
model = Model(:TestModel)
node  = addnode!(model,𝕣[0,0])
e     = addelement!(model,Hold,[node];field=:tx)
```

関連情報: [`DofConstraint`](@ref), [`DofLoad`](@ref), [`DofCost`](@ref) 
