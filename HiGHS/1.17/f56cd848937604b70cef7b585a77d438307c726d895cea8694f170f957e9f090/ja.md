```
Highs_changeColIntegrality(highs, col, integrality)
```

列の整数性を変更します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `col`: 変更する列のインデックス。
  * `integrality`: `kHighsVarType` 定数の形式での列の新しい整数性。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
