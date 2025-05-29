```
Highs_setBasis(highs, col_status, row_status)
```

列と行の基準ステータスをモデルに渡すことで、基本的な実行可能解を設定します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `col_status`: `kHighsBasisStatus`定数の形式で列基準ステータスを持つ長さ[num_col]の配列
  * `row_status`: `kHighsBasisStatus`定数の形式で行基準ステータスを持つ長さ[num_row]の配列

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
