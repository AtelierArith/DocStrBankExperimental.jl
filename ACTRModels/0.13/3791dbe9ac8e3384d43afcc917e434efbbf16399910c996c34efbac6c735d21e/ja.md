```
first_chunk(d::Declarative; criteria...)
```

条件に一致するメモリ内の最初のチャンクを返します

# 引数

  * `d::Declarative`: 宣言型メモリオブジェクト

# キーワード

  * `check_value=true`: スロット値をチェックする
  * `criteria...`: チャンクに一致するための条件に対応するオプションのキーワード引数
