```
gettreepublink(client::PCloudClient; kwargs...)
```

要求されたツリーによって定義された仮想フォルダーへの公開リンクを作成し、返します。

ツリーは以下のパラメータによって識別されます：

  * `fileids`: カンマ区切りのfileids
  * `folderids`: カンマ区切りのfolderids
  * `folderid:`: 1つのfolderidのみ - フォルダーの内容がフォルダー自体の代わりに仮想フォルダーにダンプされます

また、仮想フォルダーの名前となる`name`パラメータが必要です。

getfilepublinkと同じオプションのパラメータがあります。

作成されたリンクは、getfolderpublinkによって返されるものと似た特性を持ちますが、1つの顕著な例外があります：

*注:* ツリーの公開リンクは、作成時点での要求されたファイルとフォルダーのスナップショットであり、その後フォルダーで発生する更新には従いません。

出典: https://docs.pcloud.com/methods/public_links/gettreepublink.html

# 引数

  * `folderid::Int`: 公開リンクのフォルダーのフォルダーID
  * `path::String`: 公開リンクのフォルダーへのパス

`path`または`folderid`を使用します。

# オプション引数

  * `expire::datetime`: リンクが無効になる日時
  * `maxdownloads::Int`: このフォルダーからの最大ダウンロード数（同じファイルでも）。
  * `maxtraffic::Int`: このリンクが消費する最大トラフィック（バイト単位、開始されたダウンロードはこの制限に収まるようにカットされません）
  * `shortlink::Int`: 設定されている場合、短いリンクも生成されます

# 出力

成功した場合、次のものを返します：

  * `linkid::Int`: この公開リンクを削除/変更するために使用できるID
  * `code::String`: 公開リンクの内容を取得するために使用できるリンクのコード（showpublink/getpublinkdownloadで）

呼び出し時に`shortlink`が設定されている場合、追加の- `linkid::Int`: この公開リンクを削除/変更するために使用できるID

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
