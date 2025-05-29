```
Highs_getRowsBySet(highs, num_set_entries, set, num_row, lower, upper, num_nz, matrix_start, matrix_index, matrix_value)
```

配列によって指定された複数の行に関連するデータを取得します。

この関数は、行が指定される方法を除いて、[`Highs_getRowsByRange`](@ref)と同じです。

### パラメータ

  * `num_set_indices`: `set`内のインデックスの数。
  * `set`: 取得する行インデックスを含むサイズ[num*set*entries]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
