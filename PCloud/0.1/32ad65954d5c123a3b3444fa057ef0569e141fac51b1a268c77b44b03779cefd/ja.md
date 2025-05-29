```
getziplink(client::PCloudClient; kwargs...)
```

ユーザーのファイルシステム内のファイルのためのzipファイルリンクを受け取ります。

getzipと同じパラメータを認識します。

定義されたツリーをパラメータとして期待します。

getzipとは異なり、getfilelinkと同じ方法でダウンロードリンク(s)を返します - パス、ホスト、および有効期限を返します。

*注 : * この呼び出しは、zipアーカイブが私たちのサーバー上で作成され、その後にダウンロードリンクが得られるため、getzipよりも効率が悪いです。私たちのサーバーがどれだけ速くても、大きなアーカイブを作成するのには時間がかかる場合があります。

パラメータ `maxspeed` は、このリンクのダウンロード速度（バイト毎秒）を制限したい場合に使用できます。

ソース: https://docs.pcloud.com/methods/archiving/getziplink.html

# オプション引数

  * `maxspeed::Int`: このリンクのダウンロード速度（バイト毎秒）を制限します。
  * `forcedownload::Int`: 設定されている場合、コンテンツタイプは 'application/octet-stream' になります。設定されていない場合は 'application/zip' になります。
  * `filename::String`: 提供される場合、これは 'Content-Disposition' ヘッダーとして返され、ブラウザがファイルをダウンロードする際にこのファイル名を採用するよう強制します。ファイル名は変更されずに渡されるため、.zip 拡張子を含む必要があります。
  * `timeoffset::String`: 希望する時間オフセット

# 出力

成功すると、ファイルを持つサーバーの配列 `hosts` を返します。

最初のサーバーは、現在のダウンロードに対して私たちが `best` と考えるものです。

`path` には、サーバーに送信すべきリクエストが含まれます。

http:// または https:// を `hosts` のいずれか（最初のもの）と `path` に連結して、URLを自分で構築する必要があります。

# 出力例

```
{
    result: 0,
    path: "/dFZ73Y0ZtdPJZ3lZZhipqC7ZNVZZmb0ZHQp8Ed85S8HL874JvyYgMY8C1tbk/My%20picture.jpg",
    expires: "Thu, 03 Oct 2013 01:06:49 +0000",
    hosts: [
        "c63.pcloud.com",
        "c1.pcloud.com"
    ]
}
```
