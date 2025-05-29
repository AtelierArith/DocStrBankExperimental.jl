```
getvideolinks(client::PCloudClient; kwargs...)
```

`fileid`（または`path`）で識別されるビデオの異なる品質/解像度バージョンの`variants`配列を返します。

ビデオの各バリアントには、`path`と`hosts`（getfilelinkと同様）、ビデオの`width`と`height`、ビデオの`duration`（文字列として送信される浮動小数点数）、ビデオのフレームレートである`fps`、それぞれ`videocodec`と`audiocodec`によってエンコードされたビデオとオーディオのビットレートを指定する`videobitrate`と`audiobitrate`があります。オリジナルのビデオバリアントの場合、`isoriginal`はtrueになります。

デフォルトでは、コンテンツサーバーはビデオファイルに適切なコンテンツタイプを送信しますが、`forcedownload`または`contenttype`のオプションパラメータで上書きできます。

オプションで`skipfilename`はgetfilelinkと同様に機能します。

出典: https://docs.pcloud.com/methods/streaming/getvideolinks.html

# 引数

  * `fileid::Int`: リネームされたファイルのID
  * `path::String`: リネームされたファイルへのパス

`fileid`または`path`を使用

# オプション引数

  * `forcedownload::Int`: Content-Type = application/octet-streamでダウンロード
  * `contenttype::String`: Content-Typeを設定
  * `maxspeed::Int`: ダウンロード速度を制限
  * `skipfilename::Bool`: 生成されたリンクにファイル名を含める

# 出力

上記の通り。

# 出力例

```
{
  "result": 0,
  "variants": [
    {
      "width": 640,
      "path": "/dFZwfHQZRRZ7Z7Z2b6cC7ZQ5ZZmb0ZK1TMI6SDeOy6pdx78UAVyfUhjd6y/Octane%20Team%202013%20Winter%20Rally%20Training.mp4",
      "fps": "25",
      "isoriginal": false,
      "height": 400,
      "videocodec": "h264",
      "expires": "Wed, 13 Nov 2013 00:28:09 +0000",
      "videobitrate": 501,
      "audiobitrate": 64,
      "audiocodec": "mp3",
      "duration": "245.4",
      "hosts": [
        "c58.pcloud.com",
        "c62.pcloud.com"
      ]
    },
    {
      "width": 1280,
      "path": "/dFZysHQZRRZ7Z7Z2b6cC7ZQ5ZZmb0Z8VoWFa3rb18W6dVJgc1O7hQdWCqV/Octane%20Team%202013%20Winter%20Rally%20Training.mp4",
      "fps": "25",
      "isoriginal": false,
      "height": 720,
      "videocodec": "h264",
      "expires": "Wed, 13 Nov 2013 00:28:09 +0000",
      "videobitrate": 1505,
      "audiobitrate": 128,
      "audiocodec": "mp3",
      "duration": "245.4",
      "hosts": [
        "c3.pcloud.com",
        "c17.pcloud.com"
      ]
    },
    {
      "rotate": 0,
      "path": "/dFZPzZRRZ7Z7Z2b6cC7ZQ5ZZmb0ZoogoFjJUdb01AMSvA1aYdHQmF9Ck/Octane%20Team%202013%20Winter%20Rally%20Training.mp4",
      "fps": "25.00",
      "isoriginal": true,
      "audiosamplerate": 48000,
      "videocodec": "h264",
      "expires": "Wed, 13 Nov 2013 00:28:09 +0000",
      "videobitrate": 5737,
      "audiocodec": "aac",
      "audiobitrate": 189,
      "width": 1280,
      "duration": "245.33",
      "height": 720,
      "hosts": [
        "c3.pcloud.com",
        "c65.pcloud.com"
      ]
    }
  ]
}
```
