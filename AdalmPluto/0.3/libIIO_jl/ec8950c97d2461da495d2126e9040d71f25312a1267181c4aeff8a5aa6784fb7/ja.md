```
C_iio_channel_get_attr(channel, index)
```

指定されたインデックスに存在するチャネル固有の属性を取得します。

# パラメータ

  * `channel::Ptr{iio_channel}` : iio_channel 構造体へのポインタ
  * `index::UInt32` : 属性に対応するインデックス

# 戻り値

  * 成功した場合、NULL で終わる文字列。
  * 失敗した場合、アサーションが有効な場合はエラーをスローします。
  * 失敗した場合、アサーションが無効な場合は空の文字列を返します。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#gafc3c52f360424c097a24d1925923d772)
