```
clear_buffer!(mod::Mod)
```

バッファからチャンクを削除し、バッファの状態を次のように設定します。

  * `empty`: true
  * `busy`: false
  * `error`: false

# 引数

  * `mod::Mod`: モジュール
