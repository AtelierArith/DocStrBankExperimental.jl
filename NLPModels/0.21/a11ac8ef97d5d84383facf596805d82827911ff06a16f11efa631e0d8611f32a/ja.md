```
DimensionError <: Exception
DimensionError(name, dim_expected, dim_found)
```

予期しない次元のエラー。出力: "DimensionError: 入力 `name` の長さは `dim_expected` であるべきであり、`dim_found` ではありません"
