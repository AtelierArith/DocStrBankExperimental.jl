```
Highs_changeRowBounds(highs, row, lower, upper)
```

行の境界を変更します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `row`: 境界を変更する行のインデックス。
  * `lower`: 新しい下限。
  * `upper`: 新しい上限。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
