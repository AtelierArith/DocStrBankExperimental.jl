```
C_iio_device_set_trigger(device, trigger)
```

指定されたデバイスにトリガーを関連付けます。

# パラメータ

  * `device::Ptr{iio_device}`  : iio_device 構造体へのポインタ
  * `trigger::Ptr{iio_device}` : 関連付けるべきトリガーに対応する iio_device 構造体へのポインタ。

# 戻り値

  * 成功した場合、0 が返されます
  * エラーの場合、負の errno コードが返されます

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga3b8d1e621357f0755925d98555f53d9a)
