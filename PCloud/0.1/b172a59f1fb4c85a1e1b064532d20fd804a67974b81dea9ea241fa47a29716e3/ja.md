```
file_size(client::PCloudClient; kwargs...)
```

指定された `fd` に対して `size`（バイト単位）と現在の `offset` を返します。

ソース: https://docs.pcloud.com/methods/fileops/file_size.html

# 引数

  * `fd::Int`: サイズとオフセットが与えられるファイルディスクリプタ

# 出力例

```
{
    result: 0,
    size: "Size of the ",
    offset: "Current offset"
}
```
