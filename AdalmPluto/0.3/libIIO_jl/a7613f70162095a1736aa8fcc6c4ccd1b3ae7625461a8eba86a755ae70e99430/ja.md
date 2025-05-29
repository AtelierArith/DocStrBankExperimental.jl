```
C_iio_buffer_step(buffer)
```

1つのチャネルの2つのサンプル間のステップサイズを取得します。

# パラメータ

  * `buffer::Ptr{iio_buffer}` : iio_buffer構造体へのポインタ

# 戻り値

  * 同じチャネルの2つの連続したサンプルのアドレスの差

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#ga5532665a8776cec1c209d6cf8d0bb409)
