```
Highs_getIntOptionValues(highs, option, current_value, min_value, max_value, default_value)
```

整数オプションの現在の値とデフォルト値を取得します

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `current_value`: オプションの現在の値へのポインタ。
  * `min_value`: オプションの最小値へのポインタ。
  * `max_value`: オプションの最大値へのポインタ。
  * `default_value`: オプションのデフォルト値へのポインタ。

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
