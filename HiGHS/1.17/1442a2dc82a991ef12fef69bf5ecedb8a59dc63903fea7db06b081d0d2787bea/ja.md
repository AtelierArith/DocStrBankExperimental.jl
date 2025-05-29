```
Highs_deleteRowsBySet(highs, num_set_entries, set)
```

インデックスの配列によって指定された複数の行を削除します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `num_set_entries`: 削除する行の数。
  * `set`: 削除する行のインデックスを持つサイズ [num*set*entries] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
