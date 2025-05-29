```
Highs_getColName(highs, col, name)
```

列の名前を取得します。

### パラメータ

  * `col`: クエリする列のインデックス。
  * `name`: 列の名前を格納するポインタ。これは長さ `kHighsMaximumStringLength` でなければなりません。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
