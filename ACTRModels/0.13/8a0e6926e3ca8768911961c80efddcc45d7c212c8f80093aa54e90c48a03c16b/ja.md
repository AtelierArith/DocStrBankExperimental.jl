```
get_chunks(d::Declarative; check_value=true, criteria...)
```

指定された基準に一致するすべてのチャンクを返します。

# 引数

  * `d::Declarative`: 宣言的メモリオブジェクト

# キーワード

  * `check_value=true`: スロット値をチェックする
  * `criteria...`: チャンクの一致に対応するオプションのキーワード引数
