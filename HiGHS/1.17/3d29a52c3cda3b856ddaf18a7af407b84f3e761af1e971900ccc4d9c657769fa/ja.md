```
Highs_addRow(highs, lower, upper, num_new_nz, index, value)
```

モデルに新しい行（線形制約）を追加します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `lower`: 行の下限。
  * `upper`: 行の上限。
  * `num_new_nz`: 行の非ゼロの数。
  * `index`: 列インデックスを持つサイズ[num*new*nz]の配列。
  * `value`: 列値を持つサイズ[num*new*nz]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
