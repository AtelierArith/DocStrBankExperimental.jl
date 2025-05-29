```
echoAmplitudes(seq::MESequence, R1::AbstractFloat, R2::AbstractFloat, numStates=nothing)
```

は、与えられた `MESequence` と与えられた緩和率 R1、R2 に対してエコー振幅を計算します。計算は拡張位相グラフ法を使用して行われます。簡単のため、瞬時パルスが仮定されています。`numStates=nothing` の場合、すべての脱相状態が考慮されます。

# 引数

  * `seq::MESequence` - パルスシーケンス
  * `R1::AbstractFloat` - 使用する R1 値 (1/T1)
  * `R2::AbstractFloat` - 使用する R2 値 (1/T2)
  * `numStates=nothing` - 考慮する脱相状態の数
