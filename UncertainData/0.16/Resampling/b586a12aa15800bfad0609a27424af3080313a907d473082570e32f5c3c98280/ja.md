```
SequentialResampling{SequentialSamplingConstraint}
```

シーケンシャルにリサンプリングを行うべきことを示します。

## フィールド

  * `sequential_constraint::SequentialSamplingConstraint`。シーケンシャルサンプリング制約、例えば `StrictlyIncreasing()`。

## 例

```julia
SequentialResampling(StrictlyIncreasing())
```
