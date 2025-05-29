```
C_iio_scan_block_get_info(scan_block, index)
```

特定のコンテキストに対する `iio_context_info` を取得します。

# パラメータ

  * `scan_block::Ptr{iio_scan_block}` : `iio_scan_block` 構造体へのポインタ
  * `index::UInt32` : コンテキストに対応するインデックス。

# 戻り値

  * 成功した場合、指定された `iio_context_info` へのポインタ
  * 失敗した場合、NULL が返され、errno が適切に設定されます

バージョン 0.20 で導入されました。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#ga98c087491e97eb7e25999e3f29263e98)
