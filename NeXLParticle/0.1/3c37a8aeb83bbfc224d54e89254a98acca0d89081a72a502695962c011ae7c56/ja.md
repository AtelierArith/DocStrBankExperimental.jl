```
multiternary(dc::DiluvianCluster, cluster::Int; maxitems=1000, norm=1.0, palette = nothing, variance = false)
```

指定されたクラスタから最も重要な次元のデータを三項図としてプロットします。`maxitems`は、非常に多くのデータポイントがある場合にプロットされるポイントの総数を制限します。`norm`は、データが1以外の何かに正規化されている場合に便利です。`palette`は、toimage(…)と同じデフォルトのパレットにデフォルト設定されるか、`Colorant[]`として指定できます。`variance`は、プロットする要素を選択するために最大平均値または最大分散のどちらが使用されるかを決定します。
