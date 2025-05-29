```
file_read(client::PCloudClient; kwargs...)
```

ファイルの現在のオフセットで最大 `count` バイトを読み取ろうとします。

もし `currentofset+count<=filesize` であれば、このメソッドはリクエストを満たし、`count` バイトを読み取ります。そうでなければ、利用可能なバイトのみを返します（これがEOF条件を発見する唯一の方法です）。

データの読み取り方法については、こちらをご覧ください。

ソース: https://docs.pcloud.com/methods/fileops/file_read.html

# 引数

  * `fd::Int`: データが読み取られるファイルディスクリプタ
  * `count::Int`: ディスクリプタから読み取るバイト数

# 出力

データを返します。
