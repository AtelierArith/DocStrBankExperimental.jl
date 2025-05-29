```
C_iio_channel_attr_write_longlong(channel, attr, value)
```

指定されたチャネル固有の属性の値を設定します。

# パラメータ

  * `channel::Ptr{iio_channel}` : iio_channel 構造体へのポインタ
  * `attr::String` : 属性の名前に対応する NULL 終端文字列
  * `value::Int64` : 属性に設定するための long long 値

# 戻り値

  * 成功した場合、0 が返されます
  * エラーの場合、負の errno コードが返されます

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#gac55cb77a1baf797e54a8a4e31b2f4680)
