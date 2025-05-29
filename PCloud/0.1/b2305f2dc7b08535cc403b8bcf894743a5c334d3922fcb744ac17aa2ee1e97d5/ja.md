```
gethlslink(client::PCloudClient; kwargs...)
```

ビデオファイルのライブストリーミング用のm3u8プレイリストを取得します。

ビデオファイルの`fileid`（または`path`）を受け取り、m3u8プレイリストをHTTPライブストリーミング用にダウンロードできるリンクを提供します（`hosts`と`path`を使用してgetfilelinkが行うのと同様に）。

オプションのパラメータは`abitrate`、`vbitrate`、`resolution`、および`skipfilename`です。

これらはgetvideolinkと同じ意味を持ちます。

デフォルトはgetvideolinkと同じです。

ソース: https://docs.pcloud.com/methods/streaming/gethlslink.html

# 引数

  * `fileid::Int`: リネームされたファイルのID
  * `path::String`: リネームされたファイルへのパス

fileidまたはpathを使用します。

# オプション引数

  * `abitrate::Int`: 音声ビットレート（キロビット単位）、16から320まで
  * `vbitrate::Int`: ビデオビットレート（キロビット単位）、16から4000まで
  * `resolution::String`: ピクセル単位、64x64から1280x960まで、WIDTHxHEIGHT
  * `skipfilename::Int`: 生成されたリンクにファイル名を含めるかどうか

# 出力

成功すると、ファイルを持つサーバーの配列`hosts`が返されます。最初のサーバーは、現在のダウンロードに対して`best`と見なされるものです。

`path`には、サーバーに送信すべきリクエストが含まれます。http://またはhttps://を`hosts`（最初のもの）と`path`に連結してURLを自分で構築する必要があります。

# 出力例

```
{
    expires: "Thu, 03 Oct 2013 01:27:42 +0000",
    result: 0,
    path: "/hash/My video.m3u8",
    hosts: [
        "c11.pcloud.com",
        "c20.pcloud.com"
    ]
}
```
