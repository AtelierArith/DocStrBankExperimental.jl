```
Highs_getRowsByMask(highs, mask, num_row, lower, upper, num_nz, matrix_start, matrix_index, matrix_value)
```

マスクによって指定された複数の行に関連するデータを取得します。

この関数は、行の指定方法を除いて、[`Highs_getRowsByRange`](@ref)と同一です。

### パラメータ

  * `mask`: 行を取得するために`1`を含む長さ[num_row]の配列で、そうでない場合は`0`を含みます。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
