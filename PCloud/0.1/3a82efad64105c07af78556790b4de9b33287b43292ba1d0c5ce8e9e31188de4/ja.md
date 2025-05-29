```
copypubfile(client::PCloudClient; kwargs...)
```

パブリックリンクから現在のユーザーのファイルシステムにファイルをコピーします。

パラメータ `code` は 'code' または 'shortcode' のいずれかである必要があります。

`code` は以下から取得できます：

getfilepublink - 単一ファイルへのリンクgetfolderpublink - フォルダへのリンクgettreepublink - ツリーへのリンクgetcollectionpublink - コレクションへのリンクリンクがフォルダへのものである場合、`fileid` も必要です。

copyfile と同様に、`topath` または `tofolderid`（オプションの `toname` 付き）を指定できます。

オプションの `noover` は通常通り機能します。

実際のダウンロードやトラフィックは発生しないため、このメソッドを使用してもパブリックリンクのダウンロードやトラフィックカウンターは増加しません。したがって、パブリックリンクのダウンロードやトラフィックのクォータが切れていても `copypubfile` を実行できます。

実装者は、getpublinkdownload がダウンロード切れやトラフィック切れを示すエラーコードを返す場合に、この関数を宣伝することを推奨します。もちろん、認証されていないユーザーはこの場合、最初に登録/ログインする必要があります。

出典: https://docs.pcloud.com/methods/public_links/copypubfile.html

# 引数

  * `code::String`: 'code' または 'shortcode' のいずれか
  * `fileid::Int`: リンクがフォルダへのものである場合のファイルID
  * `path::String`: 対象ファイルへのパス
  * `tofolderid::Int`: 宛先フォルダのID
  * `topath::String`: 宛先パス

すべてが単一のメソッド呼び出しで必要なわけではありません。

# オプション引数

  * `toname::String`: 宛先ファイルの名前。省略した場合、元のファイル名が使用されます。
  * `noover::Int`: これが設定されていて、指定された名前のファイルがすでに存在する場合、上書きは行われません。

# 出力

成功した場合、パブリックリンクから現在のユーザーのアカウントにファイルをコピーし、新しいファイルの `metadata` を返します。

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
