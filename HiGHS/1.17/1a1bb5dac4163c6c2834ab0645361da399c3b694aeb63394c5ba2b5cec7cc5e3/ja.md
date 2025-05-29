```
Highs_getBasis(highs, col_status, row_status)
```

基本的な実行可能解を持つ線形計画法において、列および行の基準ステータスを取得します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `col_status`: 列基準ステータスを `kHighsBasisStatus` 定数の形式で埋めるための長さ [num_col] の配列。
  * `row_status`: 行基準ステータスを `kHighsBasisStatus` 定数の形式で埋めるための長さ [num_row] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
