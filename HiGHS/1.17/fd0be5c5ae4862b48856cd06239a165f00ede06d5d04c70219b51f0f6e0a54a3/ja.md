```
Highs_writeOptionsDeviations(highs, filename)
```

非デフォルトオプションの値をファイルに書き込みます。

これは[`Highs_writeOptions`](@ref)に似ていますが、非デフォルト値を持つオプションのみが`filename`に書き込まれます。

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `filename`: オプションを書き込むファイル名。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
