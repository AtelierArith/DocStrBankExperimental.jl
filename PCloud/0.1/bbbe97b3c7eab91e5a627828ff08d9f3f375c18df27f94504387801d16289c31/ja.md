```
file_truncate(client::PCloudClient; kwargs...)
```

ファイルサイズを `length` バイトに設定します。

`length` がファイルサイズより小さい場合、余分なデータはファイルから切り取られます。それ以外の場合、ファイルの内容は必要に応じてゼロで拡張されます。

現在のオフセットは変更されません。

ソース: https://docs.pcloud.com/methods/fileops/file_truncate.html

# 引数

  * `fd::Int`: サイズとオフセットが指定されているファイルディスクリプタ
  * `length::Int`: ファイルサイズを設定するバイト数

# 出力例

```
{
    result: 0
}
```
