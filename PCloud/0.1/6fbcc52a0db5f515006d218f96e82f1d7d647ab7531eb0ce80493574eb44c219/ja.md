```
listpublinks(client::PCloudClient; kwargs...)
```

現在のユーザーの公開リンクのリストを返します

パラメータはありません

ソース: https://docs.pcloud.com/methods/public_links/listpublinks.html

# 出力

ユーザーのすべての公開リンクを配列 `publinks` で返します。各リンクには以下のフィールドが提供されます：

  * `linkid::Int`: このIDはリンクを削除または変更するために使用できます
  * `code::String`: getfilepublinkを参照
  * `link::String`: getfilepublinkを参照
  * `created::datetime`: リンク作成の日付
  * `modified::datetime`: 最後のリンク変更の日付
  * `metadata::contents`: リンクが指すオブジェクトのメタデータ（ディレクトリにはありません）
  * `downloads::Int`: ダウンロード数
  * `traffic::Int`: このリンクによって消費されたトラフィック（バイト）

リンクにショートリンクがある場合：

  * `shortcode::String`: getfilepublinkを参照

      * `shortlink::String`: getfilepublinkを参照

リンクにショートリンクがある場合：

  * `expires::datetime`: リンクが期限切れになる日付/時間（または期限切れ）

リンクにダウンロード制限がある場合：

  * `maxdownloads::Int`: このリンクの最大ダウンロード数

リンクにトラフィック制限がある場合：

  * `maxtraffic::Int`: このリンクの最大トラフィック

期限切れまたはダウンロードまたはトラフィック制限に達したリンクを検出し、適切に表示するのは実装に依存します。

# 出力例

```
{
    result: 0,
    publinks: [
        {
            downloads: 0,
            created: "Thu, 03 Oct 2013 13:06:04 +0000",
            link: "https://my.pcloud.com/#page=publink&code=fileCode",
            modified: "Thu, 03 Oct 2013 13:06:04 +0000",
            code: "fileCode",
            traffic: 2027520,
            linkid: linkid,
            metadata: {
                parentfolderid: 21721,
                created: "Wed, 18 Sep 2013 10:18:15 +0000",
                icon: "audio",
                size: 17675824,
                album: "Simple Album",
                artist: "pCloud",
                trackno: 1,
                isfolder: false,
                contenttype: "audio/mpeg",
                genre: "Audio",
                isshared: false,
                thumb: true,
                ismine: true,
                modified: "Wed, 18 Sep 2013 10:19:05 +0000",
                title: "Simple Audio",
                category: 3,
                hash: 6343095883282229000,
                name: "Simple Audio.mp3",
                fileid: 618279,
                id: "f618279"
            }
        },
        {
            downloads: 0,
            created: "Thu, 03 Oct 2013 13:11:44 +0000",
            link: "https://my.pcloud.com/#page=publink&code=folderCode",
            modified: "Thu, 03 Oct 2013 13:11:44 +0000",
            code: "folderCode",
            traffic: 0,
            linkid: linkid,
            metadata: {
                isfolder: true,
                folderid: 21721,
                isshared: true,
                thumb: false,
                modified: "Wed, 18 Sep 2013 10:25:57 +0000",
                parentfolderid: 0,
                created: "Wed, 18 Sep 2013 10:18:14 +0000",
                ismine: true,
                icon: "folder",
                name: "Simple Folder",
                id: "d21721"
            }
        }
    ]
}
```
