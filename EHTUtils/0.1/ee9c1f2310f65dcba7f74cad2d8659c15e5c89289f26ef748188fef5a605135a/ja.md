```
mjd2hour(mjd, refmjd=nothing)
```

与えられた mjd の配列を utc 時間に変換します。

  * `mjd::AbstractArray`: 修正ユリウス日の日付の入力配列。
  * `refmjd::Number`: 参照日。デフォルトは `floor(minimum(mjd))` に設定されています。
