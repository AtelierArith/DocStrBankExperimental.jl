```
load_logger_from_config(file_path::AbstractString)::TeeLogger
```

設定ファイルパスから結合ロガーを作成します。

### 注意

結合ロガーは、結合ロガーに含まれるすべてのロガーに同時に同じログメッセージを送信できる `TeeLogger` 構造体です。
