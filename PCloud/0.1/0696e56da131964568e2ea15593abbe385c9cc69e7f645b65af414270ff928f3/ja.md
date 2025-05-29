```
extractarchive(client::PCloudClient; kwargs...)
```

ユーザーのファイルシステムからアーカイブファイルを抽出します。

アーカイブファイルの通常の `fileid` または `path` と、宛先フォルダの `tofolderid` または `topath` をパラメータとして期待します。

アーカイブがパスワードで保護されている場合は、`password` パラメータを提供する必要があります。そうでない場合、エラー番号 7009 が返されます。実装はこのエラーコードを期待し、発生した場合はユーザーにパスワードを促し、抽出プロセスを再試行する必要があります。

このメソッドは約 2 秒間抽出プロセスを実行します。これらの 2 秒以内に完了した場合、レスポンスの `finished` は true に設定されます。そうでない場合、`finished` は false となり、`progresshash` が提供されます。この値は、抽出プロセスの監視を続けるために `extractarchiveprogress` に渡すことができます。この場合、現在のサーバーに関する情報も `currentserver` によって提供されるのと同じ方法で返されます。抽出の監視は、`hostname` で返されたのと同じサーバーにリクエストを送信することによってのみ行うことができます。

`nooutput` が設定されていない限り、このメソッドは抽出プログラムの出力である行の `output` 配列も返します（末尾に改行はありません）。`lines` で返される数値は、`extractarchiveprogress` に同じ出力行を再度返さないよう指示するために使用できます。

出典: https://docs.pcloud.com/methods/archiving/extractarchive.html

# オプション引数

  * `nooutput::Bool`: 設定されている場合、抽出出力は返されません
  * `overwrite::String`: 抽出するファイルがフォルダに既に存在する場合の処理を指定します。'rename'（デフォルト）、'overwrite'、'skip' のいずれかです
  * `password::String`: パスワード保護されたアーカイブを抽出するために使用するパスワード

# 出力

上記の通りです。

# 出力例

```
{
  "progresshash": "KooPMKmcEBp",
  "ip": "204.155.151.23",
  "hostname": "api5.pcloud.com",
  "ipv6": "::1",
  "result": 0,
  "lines": 10,
  "ipbin": "204.155.151.45",
  "finished": false,
  "output": [
    "Titov.zip: Zip",
    "  Titov/_ART5055.jpg  (1681557 B)... OK.",
    "  Titov/_ART5059.jpg  (1713601 B)... OK.",
    "  Titov/_ART5063.jpg  (1811854 B)... OK.",
    "  Titov/_ART5069.jpg  (1918700 B)... OK.",
    "  Titov/_ART5071.jpg  (1701381 B)... OK.",
    "  Titov/_ART5074.jpg  (1678731 B)... OK.",
    "  Titov/_ART5076.jpg  (1658403 B)... OK.",
    "  Titov/_ART5079.jpg  (1728540 B)... OK.",
    "  Titov/_ART5094.jpg  (1745843 B)... OK."
  ]
}
```
