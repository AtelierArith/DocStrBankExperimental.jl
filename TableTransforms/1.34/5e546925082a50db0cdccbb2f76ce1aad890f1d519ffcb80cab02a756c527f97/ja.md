```
Filter(pred)
```

テーブルをフィルタリングし、述語 `pred` が `true` である行のみを返します。

# 例

```julia
Filter(row -> sum(row) > 10)
Filter(row -> row.a == true && row.b < 30)
Filter(row -> row."a" == true && row."b" < 30)
Filter(row -> row[1] == true && row[2] < 30)
Filter(row -> row[:a] == true && row[:b] < 30)
Filter(row -> row["a"] == true && row["b"] < 30)
```

## 注意事項

  * テーブルのスキーマは変換によって保持されます。
