```
copyfile(client::PCloudClient; kwargs...)
```

1つのファイルを取り、ユーザーのファイルシステム内で別のファイルとしてコピーします。

`fileid`または`path`を使用してソースファイルを特定し、`tofolderid`+`toname`または`topath`を使用して宛先ファイル名を特定することを期待します。

`toname`が省略された場合、元のファイル名が使用されます。

`topath`の最後の文字が'/'（スラッシュ）の場合も同様で、ターゲットフォルダのみを特定します。ターゲットファイルは別の新しく作成された（古いファイルが上書きされない限り、現在の作成時間を持つ）独立したファイルになります。

ソースファイルまたは宛先ファイルのいずれかに対する将来の操作は、もう一方を変更することはありません。

この呼び出しは、他の誰かのファイル（あなたと共有された）から公開リンクを作成したいときに便利です。

出典: https://docs.pcloud.com/methods/file/copyfile.html

# 引数

  * `fileid::Int`: ターゲットファイルのID
  * `path::String`: ターゲットファイルへのパス
  * `tofolderid::Int`: 宛先フォルダのID
  * `topath::String`: 宛先パス

すべてが単一のメソッド呼び出しで必要なわけではありません

# オプション引数

  * `toname::String`: 宛先ファイルの名前。省略された場合、元のファイル名が使用されます
  * `noover::Int`: これが設定されていて、指定された名前のファイルがすでに存在する場合、上書きは行われません
  * `mtime::Int`: 設定されている場合、ファイルの修正時間が設定されます。Unix時間の秒である必要があります。
  * `ctime::Int`: 設定されている場合、ファイルの作成時間が設定されます。ctimeを設定するにはmtimeを提供する必要があります。Unix時間の秒である必要があります。

# 出力

成功した場合、宛先ファイルのメタデータ（コピー結果）が返されます。

# 出力例

```
{
    "result": 0,
    "metadata": {
        "category": 1,
        "width": 900,
        "thumb": true,
        "created": "Wed, 02 Oct 2013 15:05:17 +0000",
        "hash": 10681749967730527559,
        "icon": "image",
        "ismine": true,
        "name": "Simple image.jpg",
        "modified": "Wed, 02 Oct 2013 15:05:17 +0000",
        "isfolder": false,
        "contenttype": "image/jpeg",
        "fileid": 1732283,
        "isshared": false,
        "id": "f1732283",
        "size": 73269,
        "parentfolderid": 28110,
        "height": 600
    }
}
```
