```
C_iio_context_set_timeout(context, timeout_ms)
```

I/O操作のタイムアウトを設定します。

# パラメータ

  * `context::Ptr{iio_context}` : iio_context構造体へのポインタ
  * `timeout_ms::UInt32` : タイムアウトが発生するまでの時間をミリ秒単位で表す正の整数。0の値はタイムアウトが発生しないことを指定するために使用されます。

# 戻り値

  * 成功した場合、0が返されます
  * エラーが発生した場合、負のerrnoコードが返されます

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Context.html#gaba3f4c4f9f885f41a6c0b9ac79b7f28d)
