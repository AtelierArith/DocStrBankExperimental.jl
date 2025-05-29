学習曲線を生成するためのDataFrameを指定されたメソッドに対して作成します。

```
lc_curve(method::LearningCurveMethod, InitialEffort, TotalUnits, Learning; LotSize=1)
```

DataFrameの列は次の通りです：

  * `Units`: 生産ユニット番号。
  * `CurvePoint`: そのユニットでの累積コスト/努力。
  * `IncrementalCost`: 前のステップからの累積コストの差。
  * `AvgCost`: その時点までの単位あたりの平均コスト。
  * `Method`: メソッドの文字列識別子。
