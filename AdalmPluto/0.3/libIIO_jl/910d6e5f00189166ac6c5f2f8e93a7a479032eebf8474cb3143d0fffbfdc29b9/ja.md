```
C_iio_device_get_channel(device, index)
```

指定されたインデックスに存在するチャネルを取得します。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `index::UInt32`           : チャネルに対応するインデックス

# 戻り値

  * 成功した場合、iio_channel 構造体へのポインタ
  * 失敗した場合、アサーションが有効な場合はエラーをスローします。
  * 失敗した場合、アサーションが無効な場合は NULL を返します。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga67289d735b7d8e1ed12ae0ea642bd1ac)
