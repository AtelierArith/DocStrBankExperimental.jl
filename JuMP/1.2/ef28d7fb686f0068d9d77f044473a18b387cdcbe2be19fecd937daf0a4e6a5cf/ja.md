```
relative_gap(model::Model)
```

`optimize!(model)` を呼び出した後の最終的な相対最適性ギャップを返します。正確な値は、最適化に使用される特定のソルバーによる MathOptInterface.RelativeGap() の実装に依存します。
