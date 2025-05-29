```
Highs_postsolve(highs, col_value, col_dual, row_dual)
```

プライマル（および場合によってはデュアル）ソリューションを使用してモデルをポストソルブします。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `col_value`: 列ソリューション値を持つ長さ[num_col]の配列。
  * `col_dual`: 列デュアル値を持つ長さ[num_col]の配列、または不明な場合はヌルポインタ。
  * `row_dual`: 行デュアル値を持つ長さ[num_row]の配列、または不明な場合はヌルポインタ。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
