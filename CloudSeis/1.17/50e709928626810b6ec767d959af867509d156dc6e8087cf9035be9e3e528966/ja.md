```
h = history!([io::CSeis|history::Dict]; kwargs...)
```

既存のCloudSeisデータセットまたは辞書の履歴を変更するか、新しい履歴辞書を作成します。

# オプションのキーワード引数

  * `process=""` データセットを生成するために実行されたプロセスの名前。
  * `process_parameters=Dict()` プロセスパラメータ。
  * `flow_parameters=Dit()` フローパラメータ。

# 注意事項

  * データセットを生成するために複数のプロセスが実行された場合（例：プロセスのフロー）、プロセスが実行された順序で`history!`を呼び出してください。
  * 履歴は、`csopen`および`cscreate`メソッドに`history`キーワード引数を介して渡すことができます。
