```
C_iio_scan_block_scan(scan_block)
```

スキャンブロックを介して利用可能なコンテキストを列挙します。

# パラメータ

  * `scan_block::Ptr{iio_scan_block}` : `iio_scan_block`構造体へのポインタ。

# 戻り値

  * 成功した場合、見つかったコンテキストの数。
  * 失敗した場合、負のエラー番号。

バージョン0.20で導入されました。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#gaee7e04572c3b4d202cd0043bb8cee642)
