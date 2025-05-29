```
file_pread(client::PCloudClient; kwargs...)
```

指定されたファイルの`offset`で最大`count`バイトを読み取ろうとします。

データの読み取り方法については、こちらをご覧ください。

ソース: https://docs.pcloud.com/methods/fileops/file_pread.html

# 引数

  * `fd::Int`: データが読み取られるファイルディスクリプタ
  * `count::Int`: ディスクリプタから読み取るバイト数
  * `offset::Int`: ファイル内の読み取り開始位置（バイト単位）

# 出力

データを返します。
