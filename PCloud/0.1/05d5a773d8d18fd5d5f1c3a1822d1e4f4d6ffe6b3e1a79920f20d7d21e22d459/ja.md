```
listuploadlinks(client::PCloudClient; kwargs...)
```

uploadlinks内のすべてのアップロードリンクをリストします。

Source: https://docs.pcloud.com/methods/upload_links/listuploadlinks.html

# 出力

各リンクについてリストします：

  * `uploadlinkid::Int`: このリンクを変更/削除するために使用できます
  * `link::String`: ファイルをアップロードできるページへの完全なリンク
  * `mail::String`: このリンクにファイルをアップロードするためにも使用できるメールアドレス
  * `code::String`: ファイルをアップロードするために使用できるリンクのコード
  * `comment::String`: アップロードリンクのコメント
  * `files::Int`: アップロードされたファイルの数
  * `space::Int`: アップロードされたファイルが占める合計スペース（バイト単位）
  * `metadata::metadata`: 対象フォルダのメタデータ
  * `created::datetime`: リンクが作成された日時
  * `last modified::datetime`: リンクが最後に変更された日時

作成時に指定された場合はオプションで:- `expire::datetime`: リンクが無効になる日時。

  * `maxspace::Int`: 最大合計サイズの制限（バイト単位）
  * `maxfiles::Int`: アップロードできるファイルの総数

# 出力例

```
{
    "result": 0,
    "uploadlinks": [
        {
            "space": 23640,
            "files": 23,
            "mail": "somewhere@u.pcloud.com",
            "maxspace": 524288000,
            "created": "Fri, 04 Oct 2013 16:26:41 +0000",
            "code": "linkCode",
            "maxfiles": 100,
            "comment": "Upload link comment",
            "link": "https://my.pcloud.com/#page=puplink&code=linkCode",
            "uploadlinkid": UploadLinkID,
            "modified": "Fri, 04 Oct 2013 16:26:41 +0000",
            "metadata": {
                "isfolder": true,
                "folderid": folderid,
                "thumb": false,
                "icon": "folder",
                "created": "Wed, 18 Sep 2013 10:18:14 +0000",
                "ismine": true,
                "isshared": true,
                "parentfolderid": 0,
                "name": "Simple Upload Place",
                "modified": "Wed, 18 Sep 2013 10:25:57 +0000",
                "id": "id"
            }
        }
    ]
}
```
