```
C_iio_scan_context_get_info_list(scan_context, context_info)
```

利用可能なコンテキストを列挙します。

# パラメータ

  * `scan_context::Ptr{iio_scan_context}` : `iio_scan_context` 構造体へのポインタ
  * `context_info::Ref{Ptr{Ptr{iio_context_info}}}` : `const struct iio_context_info **` 型の変数へのポインタ。成功した場合、指し示す変数が初期化されます。

# 戻り値

  * 成功した場合、見つかったコンテキストの数。
  * 失敗した場合、負のエラー番号。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Scan.html#ga5d364d8d008bdbfe5486e6329d06257f)
