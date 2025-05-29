```
savezipprogress(client::PCloudClient; kwargs...)
```

ユーザーのファイルシステムでファイルを圧縮するプロセスの進行状況を取得します。

このプロセスは、savezipメソッドで開始されます。圧縮された各ファイルについて進行状況が更新されます。`files`が結果の`totalfiles`と等しくなったときに、プロセスは完了としてマークされる可能性があります。

`progresshash`をパラメータとして期待します - 進行状況を観察する意図でsavezipに渡されるキーです。

savezipの各呼び出しに対して異なる`progresshash`を使用してください。

出典: https://docs.pcloud.com/methods/archiving/savezipprogress.html

# オプション引数

  * `progresshash::String`: 圧縮プロセスを監視するためのキー。

# 出力

そのような圧縮プロセスが存在する場合、メソッドは次のものを返します：

  * `files::Int`: すでに圧縮されたファイルの数。
  * `totalfiles::Int`: 圧縮されるべきファイルの総数。
  * `bytes::Int`: すでに圧縮されたファイルのサイズ。
  * `totalfiles::Int`: 圧縮されるべきファイルの総サイズ。

# 出力例

```
{
    "result": 0,
    "files": 34,
    "totalfiles": 129,
    "bytes": 263473,
    "totalbytes": 54750979
}
```
