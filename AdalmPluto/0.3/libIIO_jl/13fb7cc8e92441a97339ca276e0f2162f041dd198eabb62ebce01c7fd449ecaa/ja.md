```
C_iio_scan_context_destroy(scan_context)
```

指定されたスキャンコンテキストを破棄します。

# パラメータ

  * `scan_context::Ptr{iio_scan_context}` : `iio_scan_context`構造体へのポインタ

# 注意

その関数の後、`iio_scan_context pointer`は無効になります。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#ga649d7821636c744753067e8301a84e6d)
