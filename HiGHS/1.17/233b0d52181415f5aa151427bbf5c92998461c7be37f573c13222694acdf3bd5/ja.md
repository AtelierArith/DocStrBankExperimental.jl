```
Highs_changeColsIntegralityByMask(highs, mask, integrality)
```

マスクによって指定された複数の列の整合性を変更します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `mask`: 列の整合性を変更する必要がある場合は 1、そうでない場合は 0 の長さ [num_col] の配列。
  * `integrality`: `kHighsVarType` 定数の形式で、列の新しい整合性を持つ長さ [num_col] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
