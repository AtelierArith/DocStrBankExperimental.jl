```
Highs_changeColsIntegralityByRange(highs, from_col, to_col, integrality)
```

隣接する複数の列の整合性を変更します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `from_col`: 整合性が変更される最初の列のインデックス。
  * `to_col`: 整合性が変更される最後の列のインデックス。
  * `integrality`: 列の新しい整合性を `kHighsVarType` 定数の形式で持つ長さ [to*col - from*col + 1] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
