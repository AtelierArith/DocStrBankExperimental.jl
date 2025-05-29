```
Highs_getColsByMask(highs, mask, num_col, costs, lower, upper, num_nz, matrix_start, matrix_index, matrix_value)
```

マスクによって指定された複数の列に関連するデータを取得します。

この関数は、列の指定方法を除いて、[`Highs_getColsByRange`](@ref)と同じです。

### パラメータ

  * `mask`: 列を取得するために `1` を含み、それ以外は `0` を含む長さ [num_col] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
