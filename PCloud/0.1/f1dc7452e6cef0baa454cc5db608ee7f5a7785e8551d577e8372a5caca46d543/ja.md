```
getvideolink(client::PCloudClient; kwargs...)
```

動画ファイルのストリーミングリンクを取得します。動画ファイルの `fileid`（または `path`）を取り、動画を低ビットレート（および/または解像度）でストリーミングできるリンクを提供します（`hosts` と `path` を使った `getfilelink` と同様）。

トランスコードされた動画は、デフォルトで x264 ビデオと mp3 オーディオを持つ FLV コンテナに入ります。動画のビットレートは、接続速度にリアルタイムで適応されます。

デフォルトでは、コンテンツサーバーは FLV ファイルに適切なコンテンツタイプを送信しますが、これを `forcedownload` または `contenttype` のオプションパラメータで上書きすることができます。

オプションで `skipfilename` は `getfilelink` と同様に機能します。

トランスコーディングに特有のオプションパラメータは次のとおりです：

  * `abitrate::Int`: オーディオビットレート（キロビット単位）、16 から 320
  * `vbitrate::Int`: ビデオビットレート（キロビット単位）、16 から 4000
  * `resolution::String`: ピクセル単位、64x64 から 1280x960、WIDTHxHEIGHT
  * `fixedbitrate::Bool`: 設定されている場合、適応ストリーミングをオフにし、ストリームは一定のビットレートになります。

ビデオビットレートは、適応ストリーミングが使用されている場合のみ初期値です。

デフォルトのパラメータ（ほとんどのケースで一般的に問題ないはず）は次のとおりです：動画解像度に変更なし（デバイスの解像度がわかっている場合は `resolution` を設定するのが良いアイデアかもしれません）接続速度に適応する初期ビデオビットレートは 1000kbit/sec128kbit のオーディオビットレート生成されたリンクは、メソッド自体ではなく、HTTP GET パラメータ `start` を受け入れます。これが存在する場合、動画のその分の秒数をスキップします。

出典: https://docs.pcloud.com/methods/streaming/getvideolink.html

# 引数

  * `fileid::Int`: リネームされたファイルの ID
  * `path::String`: リネームされたファイルへのパス

fileid または path を使用

# オプション引数

  * `forcedownload::Int`: Content-Type = application/octet-stream でダウンロード
  * `contenttype::String`: Content-Type を設定
  * `maxspeed::Int`: ダウンロード速度を制限
  * `skipfilename::Int`: 生成されたリンクにファイル名を含める
  * `abitrate::Int`: オーディオビットレート（キロビット単位）、16 から 320
  * `vbitrate::Int`: ビデオビットレート（キロビット単位）、16 から 4000
  * `resolution::String`: ピクセル単位、64x64 から 1280x960、WIDTHxHEIGHT
  * `fixedbitrate::Bool`: 設定されている場合、適応ストリーミングをオフにし、ストリームは一定のビットレートになります。

# 出力

成功すると、ファイルを持つサーバーの配列 `hosts` を返します。最初のサーバーは、現在のダウンロードに対して `最適` と見なされるものです。

`path` には、サーバーに送信するリクエストが含まれます。http:// または https:// を `hosts`（最初のもの）と `path` に連結して URL を自分で構築する必要があります。

# 出力例

```
{
    "result": 0,
    "expires": "Thu, 03 Oct 2013 01:17:11 +0000",
    "path": "/hash/My video.mp4",
    "hosts": [
        "c11.pcloud.com",
        "c20.pcloud.com"
    ]
}
```
