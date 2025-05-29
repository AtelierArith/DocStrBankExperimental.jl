```
getpublinkdownload(client::PCloudClient; kwargs...)
```

ファイルをダウンロードできるリンクを返します。

パラメータ `code` は 'code' または 'shortcode' のいずれかである必要があります。

`code` は以下から取得できます：

getfilepublink - 単一ファイルへのリンク

getfolderpublink - フォルダへのリンク

gettreepublink - ツリーへのリンク

getcollectionpublink - コレクションへのリンク

リンクがフォルダへのものである場合、`fileid` も必要です。

オプションのパラメータ

*forcedownload*

*contenttype*

*skipfilename*

*maxspeed* は getfilelink で説明されている通りに動作します。

この呼び出しは意図的に showpublink から分割されています。

ダウンロードするつもりのないファイルのダウンロードリンクを取得することは

*悪い行動* と見なされます。

`getpublinkdownload` は、ユーザーが実際にファイルをダウンロードする意図があるときに呼び出されるべきです。

出典: https://docs.pcloud.com/methods/public_links/getpublinkdownload.html

# 引数

  * `code::String`: 'code' または 'shortcode' のいずれか
  * `fileid::Int`: フォルダへのリンクの場合のファイルID

# オプション引数

  * `forcedownload::Int`: 'Content-Type' = 'application/octet-stream' でダウンロード
  * `contenttype::String`: 'Content-Type' を設定
  * `maxspeed::Int`: ダウンロード速度を制限
  * `skipfilename::Int`: 生成されたリンクにファイル名を含める

# 出力

ファイルをダウンロードできるリンクを返します（`getfilelink` と同様に `hosts`、`path`、および `expire` が返されます）。

# 出力例

```
{
    result: 0,
    path: "/hash/My%20picture.jpg",
    expires: "Thu, 03 Oct 2013 01:06:49 +0000",
    hosts: [
        "c63.pcloud.com",
        "c1.pcloud.com"
    ]
}
```
