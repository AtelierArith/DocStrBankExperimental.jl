```
Highs_changeColsCostByMask(highs, mask, cost)
```

マスクによって指定された複数の列のコストを変更します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `mask`: 列のコストを変更する必要がある場合は1、そうでない場合は0の長さ[num_col]の配列。
  * `cost`: 新しいコストの長さ[num_col]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
