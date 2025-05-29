```
Highs_getColsBySet(highs, num_set_entries, set, num_col, costs, lower, upper, num_nz, matrix_start, matrix_index, matrix_value)
```

配列によって指定された複数の列に関連するデータを取得します。

この関数は、列の指定方法を除いて、[`Highs_getColsByRange`](@ref)と同じです。

### パラメータ

  * `num_set_indices`: `set`内のインデックスの数。
  * `set`: 取得する列インデックスを持つサイズ[num*set*entries]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
