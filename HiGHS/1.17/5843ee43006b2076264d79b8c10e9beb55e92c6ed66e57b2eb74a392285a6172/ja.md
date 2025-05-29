```
Highs_addVars(highs, num_new_var, lower, upper)
```

モデルに複数の変数を追加します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `num_new_var`: 追加する新しい変数の数。
  * `lower`: 下限を持つサイズ[num*new*var]の配列。
  * `upper`: 上限を持つサイズ[num*new*var]の配列。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
