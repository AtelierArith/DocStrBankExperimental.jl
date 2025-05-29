```
C_iio_device_get_attr(device, index)
```

指定されたインデックスに存在するデバイス固有の属性を取得します。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `index::UInt32`           : 属性に対応するインデックス

# 戻り値

  * 成功した場合、NULL で終わる文字列。
  * 失敗した場合、アサーションが有効な場合はエラーをスローします。
  * 失敗した場合、アサーションが無効な場合は空の文字列を返します。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga70b03d4cb3cc3c4fb1b6451764c8ccec)
