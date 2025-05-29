```
Highs_getColIntegrality(highs, col, integrality)
```

列の整数性を取得します。

### パラメータ

  * `col`: クエリする列のインデックス。
  * `integrality`: 列の整数性を格納する整数。この整数は `kHighsVarTypeXXX` 定数のいずれかです。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
