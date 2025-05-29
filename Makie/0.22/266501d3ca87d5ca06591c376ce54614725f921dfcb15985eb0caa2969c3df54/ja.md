```
Legend(fig_or_scene, axis::Union{Axis, Scene, LScene}, title = nothing; merge = false, unique = false, kwargs...)
```

`label` 属性が設定されている `axis` のすべてのプロットから単一グループの凡例を作成します。

`merge` が `true` の場合、同じラベルを持つすべてのプロットオブジェクトは、1つの凡例エントリに重ねられます。`unique` が `true` の場合、同じプロットタイプとラベルを持つすべてのプロットオブジェクトは1つの出現に減らされます。
