```
Highs_getBasisInverseRow(highs, row, row_vector, row_num_nz, row_index)
```

逆基底行列 $B^{-1}$ の行を取得します。

$$
B
$$

行列の説明については [`Highs_getBasicVariables`](@ref) を参照してください。

配列 `row_vector` と `row_index` は [num*row] の長さで割り当てられている必要があります。ただし、実際に格納されている非ゼロ要素の数は `row*num_nz` で確認してください。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `row`: 計算する行のインデックス。
  * `row_vector`: 非ゼロ要素の値を格納するための [num_row] の長さの配列。
  * `row_num_nz`: 行内の非ゼロの数。
  * `row_index`: 非ゼロ要素のインデックスを格納するための [num_row] の長さの配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
