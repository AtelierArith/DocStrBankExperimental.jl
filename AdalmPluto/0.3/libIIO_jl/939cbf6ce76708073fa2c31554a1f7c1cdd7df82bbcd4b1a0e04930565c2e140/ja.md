```
C_iio_channel_read!(chn, buf, dst)
```

指定されたチャネルのサンプルをデマルチプレックスして変換します。

# パラメータ

  * `chn::Ptr{iio_channel}` : iio_channel 構造体へのポインタ
  * `buf::Ptr{iio_buffer}` : iio_buffer 構造体へのポインタ
  * `dst::Array{UInt8}` : 変換されたデータが格納される配列

# 戻り値

  * dst に書き込まれた変換データのサイズ（バイト単位）

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga5c01edc37b0b57aef503abd5989a6a30)
