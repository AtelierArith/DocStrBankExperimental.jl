```
returnlevel(fm::pwmAbstractExtremeValueModel{BlockMaxima, T} where T<:Distribution, returnPeriod::Real)::ReturnLevel
```

フィットしたモデル `fm` から、信頼レベル `confidencelevel` に対応するリターン期間 `returnPeriod` に対するリターンレベルの信頼区間を計算します。
