```
GI = rasterzones(GI::GItype, shapes::GDtype, fun::Function; touches=false)
```

または

```
GI = rasterzones(fun::Function, GI::GItype, shapes::GDtype; touches=false)
```

GMTdataset `shapes` のポリゴン内にあるグリッドまたは画像 `GI` の要素に適用された `fun` の統計を計算します。詳細については `rasterzones!` のドキュメントを参照してください。この関数の違いは、入力を変更するのではなく、新しいグリッド/画像を返すことです。
