```
C_iio_buffer_first(buffer, channel)
```

バッファ内のチャネルの最初のサンプルを見つけます。

# パラメータ

  * `buffer::Ptr{iio_buffer}` : iio_buffer 構造体へのポインタ
  * `channel::Ptr{iio_channel}` : iio_channel 構造体へのポインタ

# 戻り値

  * 見つかった最初のサンプルへのポインタ、または指定されたチャネルのサンプルがバッファに存在しない場合はバッファの終わりへのポインタ

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#ga000d2f4c8b72060db1c38ec905bf4156)
