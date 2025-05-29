```
getfolderpublink(client::PCloudClient; kwargs...)
```

フォルダへの公開リンクを作成して返します。

フォルダは `folderid` または `path` によって識別されます。

getfilepublink と同じオプションのパラメータがあります。

この場合の `maxdownloads` は、このフォルダからのダウンロードの総数を制限します（同じファイルに対しても）。

出典: https://docs.pcloud.com/methods/public_links/getfolderpublink.html

# 引数

  * `folderid::Int`: 公開リンクのフォルダのフォルダID
  * `path::String`: 公開リンクのフォルダへのパス

`path` または `folderid` を使用してください。

# オプションの引数

  * `expire::datetime`: リンクが無効になる日時
  * `maxdownloads::Int`: このフォルダからのダウンロードの最大数（同じファイルに対しても）。
  * `maxtraffic::Int`: このリンクが消費する最大トラフィック（バイト単位、開始されたダウンロードはこの制限に収まるようにカットされません）
  * `shortlink::Int`: 設定されている場合、短いリンクも生成されます。

# 出力

成功した場合、次のものを返します。

  * `linkid::Int`: この公開リンクを削除/変更するために使用できるID
  * `code::String`: 公開リンクの内容を取得するために使用できるリンクのコード（showpublink/getpublinkdownloadを使用）

呼び出し時に `shortlink` が設定されている場合、追加の - `linkid::Int`: この公開リンクを削除/変更するために使用できるID

  * `shortcode::String`: showpublink/getpublinkdownload に渡すことができる短いコード
  * `shortlink::String`: shortcode が追加された pc.cd ドメインへの完全な https リンク

# 出力例

```
{
    "result": 0,
    "linkid": Link ID,
    "link": "https://my.pcloud.com/#page=publink&code=LinkCode",
    "code": "LinkCode"
}
```
