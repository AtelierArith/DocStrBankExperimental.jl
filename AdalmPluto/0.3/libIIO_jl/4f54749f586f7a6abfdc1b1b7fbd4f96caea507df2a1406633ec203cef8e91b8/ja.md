```
C_iio_channel_attr_get_filename(channel, attr)
```

属性のファイル名を取得します。

# パラメータ

  * `channel::Ptr{iio_channel}` : iio_channel 構造体へのポインタ
  * `attr::String` : 属性の名前に対応する NULL 終端の文字列

# 戻り値

  * 成功した場合、NULL 終端の文字列
  * 属性名が不明な場合、NULL が返されます。アサーションが有効な場合は、代わりにエラーがスローされます。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#gab6462404bb6667e9e9241a18e09a1638)
