```
returnlevel(fm::pwmAbstractExtremeValueModel{ThresholdExceedance, T} where T<:Distribution, threshold::Real, nobservation::Int,
    nobsperblock::Int, returnPeriod::Real)::ReturnLevel
```

フィットしたモデル `fm` からリターン期間 `returnPeriod` に対応するリターンレベルを計算します。

しきい値はスカラーである必要があります。可変のしきい値はまだ実装されていません。
