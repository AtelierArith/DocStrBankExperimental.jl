```
getfilelink(client::PCloudClient; kwargs...)
```

ファイルのダウンロードリンクを取得します。`fileid`（または`path`）をパラメータとして受け取り、ファイルをダウンロードできるリンクを提供します。

オプションのパラメータ`forcedownload`が設定されている場合、ファイルはコンテンツサーバーによってcontent type application/octet-streamで提供され、通常はユーザーエージェントにファイルを保存させることを強制します。

また、`contenttype`パラメータを提供して、コンテンツサーバーに送信してほしいContent-Typeを指定することもできます。これらのパラメータが設定されていない場合、コンテンツタイプはファイルの拡張子に依存します。

`maxspeed`パラメータは、このダウンロードのダウンロード速度（バイト毎秒）を制限したい場合に使用できます。

最後に、`skipfilename`を設定すると、生成されるリンクにファイル名が含まれなくなります。

出典: https://docs.pcloud.com/methods/streaming/getfilelink.html

# 引数

  * `fileid::Int`: リネームされたファイルのID
  * `path::String`: リネームされたファイルのパス

fileidまたはpathを使用

# オプション引数

  * `forcedownload::Int`: Content-Type = application/octet-streamでダウンロード
  * `contenttype::String`: Content-Typeを設定
  * `maxspeed::Int`: ダウンロード速度を制限
  * `skipfilename::Int`: 生成されたリンクにファイル名を含める

# 出力

成功すると、ファイルを持つサーバーの配列`hosts`が返されます。最初のサーバーは、現在のダウンロードに対して`best`と見なされるものです。

`path`には、サーバーに送信すべきリクエストが含まれます。

http://またはhttps://を`hosts`（最初のもの）と`path`を連結してURLを自分で構築する必要があります。

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
