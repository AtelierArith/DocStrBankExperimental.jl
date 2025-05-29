```
Highs_addCol(highs, cost, lower, upper, num_new_nz, index, value)
```

モデルに新しい列（変数）を追加します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `cost`: 列の目的係数。
  * `lower`: 列の下限。
  * `upper`: 列の上限。
  * `num_new_nz`: 列の非ゼロの数。
  * `index`: 行インデックスを持つサイズ[num*new*nz]の配列。
  * `value`: 行値を持つサイズ[num*new*nz]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
