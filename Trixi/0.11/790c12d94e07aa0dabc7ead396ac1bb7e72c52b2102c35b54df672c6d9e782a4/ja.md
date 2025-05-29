```
IndicatorMax(equations::AbstractEquations, basis; variable)
IndicatorMax(semi::AbstractSemidiscretization; variable)
```

要素内の`variable`の最大値を返すシンプルなインジケーター。AMRで使用するために構築する場合は、`semi`を渡します。ショックキャプチャ用にこのインジケーターを使用する場合は、`equations`と`basis`を渡します。
