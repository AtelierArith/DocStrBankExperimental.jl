```
get_chunks(actr::AbstractACTR, funs...; check_value=true, criteria...)
```

指定された基準に一致するすべてのチャンクを返します。`funs...`は一致関数として使用されます。

# 引数

  * `actr::AbstractACTR`: ACT-Rモデルオブジェクト
  * `funs...`: 関数のリスト

# キーワード

  * `check_value=true`: スロット値をチェック
  * `criteria...`: チャンクの一致に対応するオプションのキーワード引数
