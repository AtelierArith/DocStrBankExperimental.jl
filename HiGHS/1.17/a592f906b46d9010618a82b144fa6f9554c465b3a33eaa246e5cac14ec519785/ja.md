```
Highs_changeColsCostByRange(highs, from_col, to_col, cost)
```

隣接する複数の列のコスト係数を変更します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `from_col`: コストが変更される最初の列のインデックス。
  * `to_col`: コストが変更される最後の列のインデックス。
  * `cost`: 新しい目的係数を持つ長さ[to*col - from*col + 1]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
