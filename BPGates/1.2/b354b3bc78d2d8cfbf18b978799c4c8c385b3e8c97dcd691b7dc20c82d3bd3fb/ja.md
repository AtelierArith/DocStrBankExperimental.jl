ベル状態にコインシデンス測定を適用します。

状態と測定結果を返します（エラーが検出された場合は `false`）。

測定された状態は 00 にリセットされます。

```jldoctest
julia> bellmeasure!(BellState([0,1,1,1]), BellMeasure(2,1))
(BellState(Bool[0, 0, 1, 1]), false)
```
