```
C_iio_buffer_destroy(buffer)
```

指定されたバッファを破棄します。

# パラメータ

  * `buffer::Ptr{iio_buffer}` : iio_buffer 構造体へのポインタ

# 注意

その関数の後、iio_buffer ポインタは無効になります。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#gaba58dc2780be63fead6f09397ce90d10)
