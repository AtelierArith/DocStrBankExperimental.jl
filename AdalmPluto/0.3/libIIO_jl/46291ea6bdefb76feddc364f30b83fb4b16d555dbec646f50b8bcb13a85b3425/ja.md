```
C_iio_channel_attr_read_bool(channel, attr)
```

指定されたチャネル固有の属性の内容を読み取ります。

# パラメータ

  * `channel::Ptr{iio_channel}` : iio_channel 構造体へのポインタ
  * `attr::String` : 属性の名前に対応する NULL 終端文字列

# 戻り値

  * 成功した場合、`(0, value::Bool)` が返されます
  * エラーの場合、`(errno, false)` が返されます。ここで errno は負のエラーコードです。2 番目の値は破棄する必要があります。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga319f39c313bbd4d331e23df51e4d3ce6)
