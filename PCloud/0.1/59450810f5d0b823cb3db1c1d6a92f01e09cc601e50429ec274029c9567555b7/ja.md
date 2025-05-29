```
listplshort(client::PCloudClient; kwargs...)
```

現在のユーザーの公開リンクのリストを返します listpublinks

各リンクには `metadata` はなく、代わりに各リンクには `isfolder` フィールドと `fileid` または `folderid` フィールドがあります。

パラメータは必要ありません。

ソース: https://docs.pcloud.com/methods/public_links/listplshort.html

# 出力

すべてのユーザーの公開リンクを配列 `publinks` で返します。各リンクには以下のフィールドが提供されます：

  * `linkid::Int`: このIDはリンクを削除または変更するために使用できます
  * `code::String`: getfilepublinkを参照
  * `link::String`: getfilepublinkを参照
  * `created::datetime`: リンク作成の日付
  * `modified::datetime`: 最後のリンク変更の日付
  * `isfolder::Bool`: リンクがフォルダの場合はtrue
  * `folderid::Int`: isfolder=trueの場合のフォルダのID
  * `fileid::Int`: isfolder=falseの場合のファイルのID
  * `traffic::Int`: このリンクによってこれまでに消費されたトラフィック（バイト）

リンクにショートリンクがある場合:- `shortcode::String`: getfilepublinkを参照

  * `shortlink::String`: getfilepublinkを参照

リンクにショートリンクがある場合:- `expires::datetime`: リンクが期限切れになる日付/時間（または期限切れ）

リンクにダウンロード制限がある場合:- `maxdownloads::Int`: このリンクの最大ダウンロード数

リンクにトラフィック制限がある場合:- `maxtraffic::Int`: このリンクの最大トラフィック

期限切れまたはダウンロードまたはトラフィック制限に達したリンクを検出し、適切に表示するのは実装に依存します。

# 出力例

```
{
    result: 0,
    publinks: [
        {
            isfolder: false,
            traffic: 2027520,
            created: "Thu, 03 Oct 2013 13:06:04 +0000",
            fileid: 618279,
            linkid: 11660,
            downloads: 0,
            modified: "Thu, 03 Oct 2013 13:06:04 +0000",
            code: "fileCode",
            id: "f618279",
            link: "https://my.pcloud.com/#page=publink&code=fileCode"
        },
        {
            isfolder: true,
            traffic: 0,
            created: "Thu, 03 Oct 2013 13:11:44 +0000",
            id: "d21721",
            linkid: 11670,
            downloads: 0,
            folderid: 21721,
            code: "folderCode",
            modified: "Thu, 03 Oct 2013 13:11:44 +0000",
            link: "https://my.pcloud.com/#page=publink&code=folderCode"
        }
    ]
}
```
