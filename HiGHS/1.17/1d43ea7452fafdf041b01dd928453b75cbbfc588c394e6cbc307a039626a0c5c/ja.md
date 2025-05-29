```
Highs_deleteRowsByRange(highs, from_row, to_row)
```

複数の隣接する行を削除します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `from_row`: 削除する最初の行のインデックス。
  * `to_row`: 削除する最後の行のインデックス。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
