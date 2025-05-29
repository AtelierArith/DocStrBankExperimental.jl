```
savezip(client::PCloudClient; kwargs...)
```

ユーザーのファイルシステムにzipファイルを作成します。

`forcedownload`および`filename`を除く、`getzip`と同じパラメータを認識します。

定義されたツリーをパラメータとして期待します。

さらに、通常の`topath`または`tofolderid`+`toname`を期待します。

出典: https://docs.pcloud.com/methods/archiving/savezip.html

# オプション引数

  * `timeoffset::String`: 希望する時間オフセット
  * `topath::String`: zipアーカイブを保存するパス
  * `tofolderid::Int`: zipアーカイブを保存するフォルダのフォルダID
  * `toname::String`: 希望するzipアーカイブのファイル名
  * `progresshash::String`: zipプロセスの進行状況を取得するためのキー 進行状況を確認したい場合は、progresshashを渡してください。これはメソッド呼び出しごとに異なります。進行状況を取得するにはsavezipprogressを使用します。

`topath`または`tofolderid`と`toname`を使用してください。

# 出力

成功した場合、zipアーカイブを作成し、その`metadata`を返します。

# 出力例

```
{
    result: 0,
    metadata: {
        parentfolderid: 0,
        category: 5,
        hash: 3415575675870461400,
        ismine: true,
        created: "Thu, 03 Oct 2013 09:47:16 +0000",
        modified: "Thu, 03 Oct 2013 09:47:16 +0000",
        contenttype: "application/zip",
        path: "/Simple archive.zip",
        name: "Simple archive.zip",
        size: 17675984,
        isfolder: false,
        isshared: false,
        fileid: 1792497,
        icon: "archive",
        thumb: false,
        id: "f1792497"
    }
}
```
