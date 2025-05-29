```
Highs_setSolution(highs, col_value, row_value, col_dual, row_dual)
```

列と行のプライマルおよびデュアルソリューション値を渡すことで、ソリューションを設定します。

利用できない値にはNULLを渡してください。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `col_value`: 列ソリューション値の長さ[num_col]の配列。
  * `row_value`: 行ソリューション値の長さ[num_row]の配列。
  * `col_dual`: 列デュアル値の長さ[num_col]の配列。
  * `row_dual`: 行デュアル値の長さ[num_row]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
