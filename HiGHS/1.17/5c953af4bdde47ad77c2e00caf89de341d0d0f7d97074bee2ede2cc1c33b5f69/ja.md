```
Highs_setCallback(highs, user_callback, user_callback_data)
```

HiGHSで使用するコールバックメソッドを設定します

### パラメータ

  * `highs`: Highsインスタンスへのポインタ。
  * `user_callback`: ユーザーコールバックへのポインタ
  * `user_callback_data`: ユーザーコールバックデータへのポインタ

### 戻り値

呼び出しが成功したかどうかを示す`kHighsStatus`定数。
