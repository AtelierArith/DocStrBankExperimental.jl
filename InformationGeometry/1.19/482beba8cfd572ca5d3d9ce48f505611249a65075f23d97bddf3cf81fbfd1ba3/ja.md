```
ModelComparison(DM1::AbstractDataModel, DM2::AbstractDataModel) -> Tuple{Int,Real}
```

両方のモデルのAICc値を最適フィットで比較し、一方のモデルが他方よりも可能性が高い確率を推定します。タプルの最初のエントリは、どのモデルが正しい可能性が高いかを返します（1または2）、一方、2番目のエントリは確率の比 `p_better/p_worse` を返します。
