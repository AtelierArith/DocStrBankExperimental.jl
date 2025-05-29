```
Highs_changeColsIntegralityBySet(highs, num_set_entries, set, integrality)
```

複数の列の整合性を、インデックスの配列によって変更します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `num_set_entries`: 変更する列の数。
  * `set`: 変更する列のインデックスを持つサイズ [num*set*entries] の配列。
  * `integrality`: `kHighsVarType` 定数の形式で、列の新しい整合性を持つ長さ [num*set*entries] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
