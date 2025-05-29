```
outcomes(o::OutcomeSpace, x)
```

与えられた [`OutcomeSpace`](@ref) に従って、入力データ `x` に現れるすべての（ユニークな）結果を返します。`probabilities_and_outcomes(o, x)[2]` と同等ですが、一部の推定器ではパフォーマンス向上のために明示的に拡張される場合があります。
