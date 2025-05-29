```
TraitTarget{T}
```

この構造体は、トレイトパラメータまたはトレイトパラメータのユニオンを保持します。

主に、`apply`のようなトレイトレベルを選択するメソッドへのディスパッチや、`target`へのパラメータとして使用されます。

## コンストラクタ

```julia
TraitTarget(GI.PointTrait())
TraitTarget(GI.LineStringTrait(), GI.LinearRingTrait()) # お好みで他のトレイトも
TraitTarget(TraitTarget(...))
# 型ベースのコンストラクタも利用可能ですが、推奨されません。
TraitTarget(GI.PointTrait)
TraitTarget(Union{GI.LineStringTrait, GI.LinearRingTrait})
# など。
```
