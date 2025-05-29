```
file_seek(client::PCloudClient; kwargs...)
```

ファイルディスクリプタの現在のオフセットを `offset` バイトに設定します。

このメソッドは、`whence` パラメータに応じて以下のモードで動作します：

  * `0`: ファイルの先頭の後に移動
  * `1`: 現在の位置の後に移動
  * `2`: ファイルの末尾の後に移動

出典: https://docs.pcloud.com/methods/fileops/file_seek.html

# 引数

  * `fd::Int`: 現在のオフセットが変更されるファイルディスクリプタ
  * `offset::Int`: 現在のオフセットを移動するバイト数のオフセット

# オプション引数

  * `whence::Int`: オフセットシークが動作するモード。デフォルト値は 0

# 出力

新しい `offset` を返します。

# 出力例

```
{
    result: 0,
    offset: 1024
}
```
