```
C_iio_channel_attr_write_raw(channel, attr, value)
```

指定されたチャネル固有の属性の値を設定します。

# パラメータ

  * `channel::Ptr{iio_channel}` : iio_channel 構造体へのポインタ
  * `attr::String` : 属性の名前に対応する NULL 終端文字列
  * `value::Ptr{Cvoid}`       : 書き込むデータへのポインタ
  * `size::Csize_t`           : 書き込むバイト数

# 戻り値

  * 成功した場合、書き込まれたバイト数
  * エラーの場合、負の errno コードが返されます

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#gacd0d3dd36bdc64a9f967e21a891230eb)
