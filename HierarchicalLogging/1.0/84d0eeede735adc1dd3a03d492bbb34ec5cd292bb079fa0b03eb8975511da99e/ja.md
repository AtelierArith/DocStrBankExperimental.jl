```
set_logger!(loggers, key, logger)
```

`loggers`内の`key`に関連付けられたロガーを`logger`に設定します。

`loggers`内の`key`に関連付けられた既存の値がある場合、それは上書きされます。`key`の新しいレベルは、`key`に関連付けられた以前のログレベルと`logger`の現在のレベルの最大値に設定されます。
