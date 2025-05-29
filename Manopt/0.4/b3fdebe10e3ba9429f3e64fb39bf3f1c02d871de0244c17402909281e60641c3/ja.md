```
RecordWhenActive <: RecordAction
```

`active` ブール値が true に設定されている場合のみ記録するレコードアクションです。これは外部から設定でき、例えばサブソルバーの録音で `RecordEvery`](@ref) によってトリガーされます。これはサブソルバーにとって完全に必要ではないかもしれませんが、決してアクセスできない値を記録することはあまり有用ではありません。

# フィールド

  * `active`:        デバッグをオン/オフするために外部から (非) 活性化できるブール値
  * `always_update`: 非正の反復 (初期化/リセット) で内部デバッグを呼び出すかどうか

# コンストラクタ

```
RecordWhenActive(r::RecordAction, active=true, always_update=true)
```
