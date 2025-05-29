```
getaudiolink(client::PCloudClient; kwargs...)
```

オーディオファイルのストリーミングリンクを取得します。オーディオ（またはビデオ）ファイルの `fileid`（または `path`）を取り、mp3形式でストリーミングできるリンクを提供します。（`hosts` と `path` を使った `getfilelink` と同様です）

オプションのパラメータは `abitrate`、`forcedownload`、および `contenttype` です。

デフォルトのビットレートは192kbitです。

ビデオからオーディオトラックを抽出するためにも使用できます。

リンク自体は `start` GETパラメータをサポートしています。このメソッドは、mp3再生のみをサポートするデバイスでFLACやその他の新しいフォーマットを再生するために使用できます。

出典: https://docs.pcloud.com/methods/streaming/getaudiolink.html

# 引数

  * `fileid::Int`: リネームされたファイルのID
  * `path::String`: リネームされたファイルへのパス

fileidまたはpathを使用します。

# オプション引数

  * `forcedownload::Int`: Content-Type = application/octet-stream でダウンロード
  * `contenttype::String`: Content-Typeを設定
  * `abitrate::Int`: 音声ビットレート（キロビット単位）、16から320の範囲

# 出力

成功すると、ファイルを持つサーバーの配列 `hosts` を返します。最初のサーバーは、現在のダウンロードに対して `best` と見なされるものです。

`path` には、サーバーに送信するリクエストが含まれます。http:// または https:// を `hosts`（最初のもの）と `path` に連結して、URLを自分で構築する必要があります。

# 出力例

```
{
    result: 0,
    expires: "Thu, 03 Oct 2013 01:23:12 +0000",
    path: "/hash/My Audio.mp3",
    hosts: [
        "c53.pcloud.com",
        "c58.pcloud.com"
    ]
}
```
