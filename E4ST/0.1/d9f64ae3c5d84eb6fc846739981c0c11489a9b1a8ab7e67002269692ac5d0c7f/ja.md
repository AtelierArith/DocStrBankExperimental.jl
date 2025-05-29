```
struct EmissionCap <: Policy
```

排出キャップ - 特定の発電機のセットに対する排出量の制限。

  * `name`: ポリシーの名前 (シンボル)
  * `emis_col`: 発電機テーブル内の排出率列の名前 (例: emis_co2) (シンボル)
  * `targets`: 年ごとのキャップターゲットのOrderedDict
  * `gen_filters`: 発電機フィルターのOrderedDict
  * `gen_cons`: EmissionCapのインスタンス化時に作成されたGenerationConstraintの修正 (設定には指定されていない)。キャップターゲットをGenerationConstraintのmax_targetsとして設定し、他のフィールドを引き継ぎます。
