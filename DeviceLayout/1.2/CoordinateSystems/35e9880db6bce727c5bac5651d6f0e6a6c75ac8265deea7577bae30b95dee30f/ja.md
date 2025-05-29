```
flatten!(c::AbstractCoordinateSystem, depth::Integer=-1, metadata_filter=nothing, max_copy=Inf)
```

階層的な `depth` まで、参照と配列を再帰的にフラット化し、それらの要素を適切な変換を施して `c` に追加します。

フラット化された参照と配列はその後破棄されます。より深い参照と配列は持ち上げられ、破棄されることはありません。

この関数は `depth == 0` の場合には効果がなく、デフォルトでは無制限の深さです。
