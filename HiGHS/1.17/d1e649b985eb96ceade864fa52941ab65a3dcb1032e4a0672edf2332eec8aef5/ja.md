```
Highs_addVar(highs, lower, upper)
```

モデルに新しい変数を追加します。

### パラメータ

  * `highs`: Highs インスタンスへのポインタ。
  * `lower`: 列の下限。
  * `upper`: 列の上限。

### 戻り値

呼び出しが成功したかどうかを示す `kHighsStatus` 定数。
