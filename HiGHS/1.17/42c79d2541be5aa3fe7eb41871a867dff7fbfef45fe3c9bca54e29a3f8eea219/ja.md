```
Highs_getReducedColumn(highs, col, col_vector, col_num_nz, col_index)
```

$$
B^{-1}A
$$

の列を計算します。

$$
B
$$

行列の説明については[`Highs_getBasicVariables`](@ref)を参照してください。

配列`col_vector`と`col_index`は、[num*row]の長さを持つように割り当てられている必要があります。ただし、実際に格納されている非ゼロ要素の数は`col*num_nz`を確認してください。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `col`: 計算する列のインデックス。
  * `col_vector`: 非ゼロ要素の値を格納するための長さ[num_row]の配列。
  * `col_num_nz`: 列内の非ゼロの数。
  * `col_index`: 非ゼロ要素のインデックスを格納するための長さ[num_row]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
