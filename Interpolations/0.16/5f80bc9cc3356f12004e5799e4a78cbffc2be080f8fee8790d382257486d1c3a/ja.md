```
ChainRulesCore.rrule(itp::AbstractInterpolation, x...)
```

ChainRulesCore.jlの`rrule`は、自動微分ライブラリとの統合のためのものです。これは、評価点`x`に対してのみ勾配を提供し、`itp`内のデータには提供しないことに注意してください。
