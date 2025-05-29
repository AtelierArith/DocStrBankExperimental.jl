```
Highs_getRowName(highs, row, name)
```

行の名前を取得します。

### パラメータ

  * `row`: クエリする行のインデックス。
  * `name`: 行の名前を格納するポインタ。これは `kHighsMaximumStringLength` の長さを持っている必要があります。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
