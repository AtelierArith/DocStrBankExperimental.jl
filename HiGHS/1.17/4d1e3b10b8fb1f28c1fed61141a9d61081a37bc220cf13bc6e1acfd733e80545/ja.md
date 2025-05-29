```
Highs_changeColBounds(highs, col, lower, upper)
```

列の変数境界を変更します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `col`: 境界を変更する列のインデックス。
  * `lower`: 新しい下限。
  * `upper`: 新しい上限。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
