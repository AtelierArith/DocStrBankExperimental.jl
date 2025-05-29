```
function evaluate!(
    result,                     # 結果のターゲット
    PE::PointEvaluator,         
    xref,                       # アイテム内のローカル座標
    item                        # アイテム番号
    ) where  {T, Tv, Ti, FEType, FEOP, AT, ACT}
```

指定されたアイテム番号のアイテム内の与えられたローカル座標でPointEvaluatorを評価します。（ローカル座標を取得するには、現在手動でCellFinderを維持する必要がありますが、これは将来的に変更される可能性があります。）
