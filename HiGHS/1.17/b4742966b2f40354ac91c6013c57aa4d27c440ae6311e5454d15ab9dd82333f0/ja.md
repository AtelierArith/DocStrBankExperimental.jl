```
Highs_deleteColsByRange(highs, from_col, to_col)
```

隣接する複数の列を削除します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `from_col`: 削除する最初の列のインデックス。
  * `to_col`: 削除する最後の列のインデックス。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
