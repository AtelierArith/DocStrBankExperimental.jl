```
Highs_addCols(highs, num_new_col, costs, lower, upper, num_new_nz, starts, index, value)
```

モデルに複数の列（変数）を追加します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `num_new_col`: 追加する新しい列の数。
  * `costs`: 目的係数を持つサイズ [num*new*col] の配列。
  * `lower`: 下限を持つサイズ [num*new*col] の配列。
  * `upper`: 上限を持つサイズ [num*new*col] の配列。
  * `num_new_nz`: 制約行列の新しい非ゼロの数。
  * `starts`: 制約係数は、配列 `starts`、`index`、および `value` によって圧縮スパース列形式の行列として与えられます。`starts` は、インデックスと値の各行の開始インデックスを持つサイズ [num*new*cols] の配列です。
  * `index`: 行インデックスを持つサイズ [num*new*nz] の配列。
  * `value`: 行値を持つサイズ [num*new*nz] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
