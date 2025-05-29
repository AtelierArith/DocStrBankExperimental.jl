```julia
renormalize!(dataset, [elements]; total=1.0)
```

`Dict` または `NamedTuple` で定義された (すなわち、成分的な) `dataset` をインプレースで正規化し、すべての `elements` (すなわち、変数 – デフォルトではデータセット内のすべてのキー) が指定された `total` (デフォルトでは `1.0`) に合計されるようにします。

各要素または変数を表す配列は、均一な長さであると仮定されます。
