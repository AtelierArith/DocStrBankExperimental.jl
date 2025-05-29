```
birthdate(n::Integer = 1; start::Date, stop::Date)
```

`start` と `stop` の日付の間に `n` の誕生日エントリを生成します。

# パラメータ

  * `n::Int = 1`: 生成する日付の数。
  * `start::Date = Date(1900, 1, 1)`: サンプリング期間の開始。
  * `stop::Date = Dates.today()`: サンプリング期間の終了。
