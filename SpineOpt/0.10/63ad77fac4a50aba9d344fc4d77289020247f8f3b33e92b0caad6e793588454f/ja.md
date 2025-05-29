```
write_report(m, url_out; <keyword arguments>)
```

与えられたSpineOptモデルから`url_out`にレポートを作成します。`url_out`に存在しない場合は新しいSpineデータベースが作成されます。

# 引数

  * `alternative::String=""`: 空でない場合、出力DBの指定された代替に結果を書き込みます。
  * `log_level::Int=3`: ログレベルを制御する整数。
