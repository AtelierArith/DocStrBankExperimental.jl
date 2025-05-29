```
Highs_getBasisSolve(highs, rhs, solution_vector, solution_num_nz, solution_index)
```

ベクトル ${b}$ に対して ${x}=B^{-1}{b}$ を計算します。

$$
B
$$

行列の説明については [`Highs_getBasicVariables`](@ref) を参照してください。

配列 `solution_vector` と `solution_index` は [num*row] の長さで割り当てられている必要があります。ただし、実際に格納されている非ゼロ要素の数は `solution*num_nz` を確認してください。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `rhs`: 右辺ベクトル $b$。
  * `solution_vector`: 非ゼロ要素の値を格納するための長さ [num_row] の配列。
  * `solution_num_nz`: 解の非ゼロの数。
  * `solution_index`: 非ゼロ要素のインデックスを格納するための長さ [num_row] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
