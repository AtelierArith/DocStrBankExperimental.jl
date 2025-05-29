```
fits_write_date(f::FITSFile)
```

FITSヘッダーに現在の日付と時刻を書き込みます。DATEキーワードがすでに存在する場合は、新しい値で置き換えられます。日付は`YYYY-MM-DDThh:mm:ss`（ISO 8601）形式で書き込まれます。
