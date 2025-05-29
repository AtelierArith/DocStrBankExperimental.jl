```
Highs_changeCoeff(highs, row, col, value)
```

制約行列の係数を変更します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `row`: 変更する行のインデックス。
  * `col`: 変更する列のインデックス。
  * `value`: 新しい制約係数。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
