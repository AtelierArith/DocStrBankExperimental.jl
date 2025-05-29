```
Highs_changeColsBoundsByRange(highs, from_col, to_col, lower, upper)
```

複数の隣接する列の変数の境界を変更します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `from_col`: 境界が変更される最初の列のインデックス。
  * `to_col`: 境界が変更される最後の列のインデックス。
  * `lower`: 新しい下限を持つ長さ [to*col - from*col + 1] の配列。
  * `upper`: 新しい上限を持つ長さ [to*col - from*col + 1] の配列。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
