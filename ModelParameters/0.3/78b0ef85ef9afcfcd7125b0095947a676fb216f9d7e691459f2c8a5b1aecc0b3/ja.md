```
stripunits(model::AbstractModel, xs)
stripunits(param::AbstractParam, x)
```

対応する単位フィールドが存在する場合、`x`または`xs`をその単位フィールドで割った値を返します。

単位フィールドが存在せず、`x`に単位がある場合は、単位付きで返されます！単位を単純にすべて削除したい場合は、`Unitful.ustrip`を使用してください。
