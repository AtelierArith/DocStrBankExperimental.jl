```
Highs_addRows(highs, num_new_row, lower, upper, num_new_nz, starts, index, value)
```

モデルに複数の行（線形制約）を追加します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `num_new_row`: 追加する新しい行の数
  * `lower`: 行の下限を持つサイズ [num*new*row] の配列。
  * `upper`: 行の上限を持つサイズ [num*new*row] の配列。
  * `num_new_nz`: 行の非ゼロの数。
  * `starts`: 制約係数は、配列 `starts`、`index`、および `value` によって圧縮スパース行形式の行列として与えられます。`starts` は、インデックスと値における各行の開始インデックスを持つサイズ [num*new*rows] の配列です。
  * `index`: 列インデックスを持つサイズ [num*new*nz] の配列。
  * `value`: 列値を持つサイズ [num*new*nz] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
