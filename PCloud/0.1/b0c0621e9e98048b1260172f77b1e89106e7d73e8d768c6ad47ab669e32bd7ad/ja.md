```
renamefile(client::PCloudClient; kwargs...)
```

ファイルの名前を変更する

`fileid` または `path` で識別されるファイルの名前を、`topath`（`topath` が新しいファイル名なしのフォルダ名の場合はスラッシュで終わる必要があります - /newpath/）または `tofolderid`/`toname` に変更（および/または移動）します（1つまたは両方を提供できます）。

宛先のファイルがすでに存在する場合、元のファイルで原子的に置き換えられます。この場合、メタデータには宛先の古いファイルの `fileid` を持つ `deletedfileid` が含まれ、元のファイルと宛先ファイルのリビジョンが統合されます。

出典: https://docs.pcloud.com/methods/file/renamefile.html

# 引数

  * `fileid::Int`: 名前が変更されたファイルのID
  * `path::String`: 名前が変更されたファイルのパス
  * `topath::String`: 名前が変更されたファイルの宛先パス
  * `tofolderid::Int`: ファイルが移動されるフォルダのID
  * `toname::String`: 名前が変更されたファイルの宛先ファイル名

fileid または path を使用

# 出力

成功した場合、マージされたファイルの場合は `deletedfileid` を含む名前が変更されたファイルの `metadata` を返します。

# 出力例

```
{
    "result": 0,
    "metadata": {
        "id": "f1729212",
        "fileid": 1729212,
        "size": 73269,
        "isfolder": false,
        "hash": 10681749967730527559,
        "isshared": false,
        "thumb": true,
        "height": 600,
        "contenttype": "image/jpeg",
        "icon": "image",
        "created": "Wed, 02 Oct 2013 14:29:11 +0000",
        "width": 900,
        "modified": "Wed, 02 Oct 2013 16:07:40 +0000",
        "ismine": true,
        "name": "My picture.jpg",
        "category": 1,
        "parentfolderid": 0
    }
}
```
