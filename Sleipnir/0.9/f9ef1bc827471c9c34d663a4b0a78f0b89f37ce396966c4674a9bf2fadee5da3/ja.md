```
trim_period(period, climate)
```

与えられた `period` を `climate` データの範囲内に収め、 hydrological years に合わせて調整します。

# 引数

  * `period::UnitRange{Date}`: 切り取る初期の日付範囲。
  * `climate::AbstractArray`: 時間次元 `Ti` を持つ気候データ配列。

# 戻り値

  * `UnitRange{Date}`: 気候データの時間範囲内に収まるように調整された日付範囲。

# 詳細

  * 気候データの開始が期間の開始より遅い場合、期間は気候データの開始年の10月1日から始まるように調整されます。
  * 気候データの終了が期間の終了より早い場合、期間は気候データの終了年の9月30日で終了するように調整されます。
