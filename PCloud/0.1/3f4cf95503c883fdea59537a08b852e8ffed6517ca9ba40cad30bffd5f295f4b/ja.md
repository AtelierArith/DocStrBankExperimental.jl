```
downloadfileasync(client::PCloudClient; kwargs...)
```

ファイルをダウンロードする

`url` パラメータに指定されたリンクから1つ以上のファイルを、`path` または `folderid` で識別されるフォルダに（両方が省略された場合はルートフォルダに）ダウンロードします。レスポンスは、ファイルがダウンロードのキューに追加されたときに受信され、ダウンロードが完了したときではありません。`progresshash` パラメータ文字列を渡すことができます。同じものを uploadprogress メソッドに渡す必要があります。uploadprogress で進行状況を監視する際には、次のフィールドが存在します：

  * `urlcount::Int`: リクエストされたURLの数
  * `urlready::Int`: すでにダウンロードされたURLの数
  * `urlworking::Int`: 現在ダウンロード中のURLの数
  * `finished::Bool`: すべてのURLがダウンロードされた場合はtrue
  * `files::array`: オブジェクトの配列

`files` の各レコードには次の情報があります：- `url::String`: URL

  * `status::String`: 次のいずれか：待機中 リンクがダウンロードの順番を待っているダウンロード中 リンクが現在ダウンロード中準備完了 URLが指すファイルはすでにダウンロード済みエラー ダウンロード中にエラーが発生（タイムアウト、404、サーバーが応答しない）
  * `size::Int`: 開始されたダウンロードに対してのみ利用可能 - サーバーが提供したContent-Length - ファイルのサイズ
  * `downloaded::Int`: 開始されたダウンロードに対してのみ利用可能 - これまでにダウンロードされたバイト数（サイズまで増加）
  * `metadata::metadata`: 準備完了のダウンロードに対してのみ利用可能 - ユーザーのファイルシステム内のファイルのメタデータ

ファイルは、指定されたURLから定義された名前で保存されます。これらの名前は、`target` パラメータを使用して設定できます。このパラメータには、希望する名前のカンマ区切りのURLエンコードされたリストが含まれている必要があります。このシーケンスのn番目の名前は、`url` パラメータのn番目のURLに与えられます。

すべてのURLに `target` で指定された名前を付けることができるわけではありません。その場合、名前を空にしておくか（ 'name%20A,,name%20C' ）、希望する最後の名前でリストを終了してください（URLはターゲット名よりも多くなる可能性があります）。

出典: https://docs.pcloud.com/methods/file/downloadfileasync.html

# 引数

  * `url::String`: 任意の量の空白で区切られたリンク

# オプション引数

  * `path::String`: ファイルをダウンロードするフォルダへのパス
  * `folderid::String`: ファイルをダウンロードするフォルダのフォルダID
  * `target::String`: ダウンロードするファイルの希望する名前

path または folderid が存在しない場合、ルートフォルダが使用されます。

# 出力

メソッドは、すべてのファイルがダウンロードされると返されます（時間がかかる場合があります）。成功した場合、すべてのダウンロードされたファイルのメタデータを含む `metadata` 配列が返されます。

# 出力例

```
{
    "result": 0,
    "metadata": [
        {
            "icon": "image",
            "path": "Simple image.jpg",
            "isshared": false,
            "ismine": true,
            "fileid": 1736716,
            "size": 15604,
            "category": 1,
            "name": "Simple image.jpg",
            "created": "Wed, 02 Oct 2013 15:57:13 +0000",
            "hash": 6306013028049022731,
            "parentfolderid": 0,
            "modified": "Wed, 02 Oct 2013 15:57:28 +0000",
            "thumb": true,
            "isfolder": false,
            "height": 300,
            "width": 222,
            "id": "f1736716",
            "contenttype": "image/jpeg"
        }
    ]
}
```
