```
get_chunks(d::Declarative, funs...; check_value=true, criteria...)
```

指定された基準に一致するすべてのチャンクを返します。`funs...`は一致関数として使用されます。

# 引数

  * `d::Declarative`: 宣言型メモリオブジェクト
  * `funs...`: 関数のリスト

# キーワード

  * `check_value=true`: スロット値をチェックする
  * `criteria...`: チャンクの一致に対応するオプションのキーワード引数
