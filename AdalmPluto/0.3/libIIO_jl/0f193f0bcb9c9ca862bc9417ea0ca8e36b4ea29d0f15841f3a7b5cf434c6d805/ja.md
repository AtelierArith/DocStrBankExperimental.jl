```
C_iio_scan_block_destroy(scan_block)
```

指定されたスキャンブロックを破棄します。

# パラメータ

  * `block::Ptr{iio_scan_block}` : `iio_scan_block`構造体へのポインタ

# 注意

この関数の後、`iio_scan_block`ポインタは無効になります。

バージョン0.20で導入されました。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#ga91f6902ca18c491f96627cadb88c5c0a)
