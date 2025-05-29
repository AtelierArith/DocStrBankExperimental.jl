```
getfilepublink(client::PCloudClient; kwargs...)
```

ファイルへの公開リンクを作成して返します。

ファイルは `fileid` または `path` で識別されます。

ソース: https://docs.pcloud.com/methods/public_links/getfilepublink.html

# 引数

  * `fileid::Int`: 公開リンクのファイルのファイルID
  * `path::String`: 公開リンクのファイルへのパス

`path` または `fileid` を使用します。

# オプション引数

  * `expire::datetime`: リンクが無効になる日時
  * `maxdownloads::Int`: このファイルの最大ダウンロード数
  * `maxtraffic::Int`: このリンクが消費する最大トラフィック（バイト単位、開始されたダウンロードはこの制限に収まるようにカットされません）
  * `shortlink::Int`: 設定されている場合、短いリンクも生成されます

# 出力

成功した場合、次のものが返されます。

  * `linkid::Int`: この公開リンクを削除/変更するために使用できるID
  * `code::String`: 公開リンクの内容を取得するために使用できるリンクのコード（showpublink/getpublinkdownloadを使用）

呼び出し時に `shortlink` が設定されている場合、追加で

  * `linkid::Int`: この公開リンクを削除/変更するために使用できるID
  * `shortcode::String`: showpublink/getpublinkdownloadに渡すことができる短いコード
  * `shortlink::String`: shortcodeが追加されたpc.cdドメインへの完全なhttpsリンク

# 出力例

```
{
    "result": 0,
    "linkid": Link ID,
    "link": "https://my.pcloud.com/#page=publink&code=LinkCode",
    "code": "LinkCode"
}
```
