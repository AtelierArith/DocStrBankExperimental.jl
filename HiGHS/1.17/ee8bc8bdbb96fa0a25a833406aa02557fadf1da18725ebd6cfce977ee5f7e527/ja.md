```
Highs_scaleRow(highs, row, scaleval)
```

定数で行をスケーリングします。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `row`: スケーリングする行のインデックス。
  * `scaleval`: 行をスケーリングするための値。`scaleval < 0` の場合、行の境界が反転します。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
