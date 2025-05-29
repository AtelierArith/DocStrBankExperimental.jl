```
dbc_send_file(path::AbstractString, filename = nothing; type = nothing)
```

ファイルをダウンロードコンポーネントが期待する形式に変換します。

# 引数

  * `path` - 送信するファイルのパス
  * `filename` - ファイルの名前。指定されていない場合は元のファイル名が使用されます
  * `type` - ファイルのタイプ（オプション、JavaScriptレイヤーのBlobに渡されます）
