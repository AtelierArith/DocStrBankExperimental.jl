```
file_checksum(client::PCloudClient; kwargs...)
```

ファイル記述子 `fd` から `offset` の `count` バイトのチェックサムを計算します。

この関数を使用して、変更されていないファイル全体のチェックサムを計算しないでください。代わりに checksumfile を使用してください。

ソース: https://docs.pcloud.com/methods/fileops/file_checksum.html

# 引数

  * `fd::Int`: チェックサムが計算されるファイル記述子
  * `count::Int`: チェックサムが計算されるバイト数
  * `offset::Int`: チェックサム計算が開始されるバイト位置

# 出力

`sha1`、`md5`、および `size` を返します。

`size` は、現在のファイルサイズを超えるバイトがチェックサムを要求されない限り、`count` と等しくなります。

# 出力例

```
{
    result: 0,
    sha1: "SHA-1 チェックサム",
    md5: "MD5 チェックサム",
    size: "チェックサムが計算されるバイト数"
}
```
