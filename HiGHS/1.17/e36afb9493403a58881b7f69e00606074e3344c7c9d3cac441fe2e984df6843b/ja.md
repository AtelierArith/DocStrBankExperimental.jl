```
Highs_scaleCol(highs, col, scaleval)
```

定数によって列をスケーリングします。

列をスケーリングすると、制約行列内の要素、変数の境界、および目的関数の係数が変更されます。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `col`: スケーリングする列のインデックス。
  * `scaleval`: 列をスケーリングするための値。`scaleval < 0`の場合、変数の境界が反転します。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
