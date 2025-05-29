```
upper(p::OrthogonalIntervalProbabilities, l, i, j)
```

ソース状態またはソース/アクションペアからターゲット状態への上限遷移確率を返します。

!!! note
    この関数はO-最大化のホットループで使用することは推奨されません。 [`IntervalProbabilities`](@ref) は下限およびギャップ遷移確率を格納しているため、上限を取得するには割り当てと計算が必要です。

