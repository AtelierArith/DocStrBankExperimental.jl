```
Highs_deleteColsByMask(highs, mask)
```

マスクによって指定された複数の列を削除します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `mask`: 列を削除する必要がある場合は1、そうでない場合は0の長さ[num_col]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
