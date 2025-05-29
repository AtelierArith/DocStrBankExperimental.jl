```
Highs_getSolution(highs, col_value, col_dual, row_value, row_dual)
```

最適化されたモデルからプライマルおよびデュアルソリューションを取得します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `col_value`: プライマル列値で埋められる長さ[num_col]の配列。
  * `col_dual`: デュアル列値で埋められる長さ[num_col]の配列。
  * `row_value`: プライマル行値で埋められる長さ[num_row]の配列。
  * `row_dual`: デュアル行値で埋められる長さ[num_row]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
