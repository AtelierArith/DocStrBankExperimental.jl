```
Highs_changeColsBoundsByMask(highs, mask, lower, upper)
```

マスクによって指定された複数の列の変数境界を変更します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `mask`: 列の境界を変更する必要がある場合は 1、そうでない場合は 0 の長さ [num_col] の配列。
  * `lower`: 新しい下限を持つ長さ [num_col] の配列。
  * `upper`: 新しい上限を持つ長さ [num_col] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
