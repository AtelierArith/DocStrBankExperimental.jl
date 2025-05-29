```
Highs_setSparseSolution(highs, num_entries, index, value)
```

部分的なプライマルソリューションを、変数のセットに対する値を渡すことで設定します。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `num_entries`: セット内の変数の数
  * `index`: セット内の変数のインデックス
  * `value`: セット内の変数の値

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
