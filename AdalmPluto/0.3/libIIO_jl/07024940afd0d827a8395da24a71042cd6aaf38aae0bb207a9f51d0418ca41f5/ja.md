```
C_iio_device_get_trigger(device)
```

指定されたデバイスのトリガーを取得します。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ

# 戻り値

  * 成功した場合、`(0, trigger::Ptr{iio_device})` が返されます。
  * エラーの場合、`(errno, NULL)` が返されます。ここで、errno は負のエラーコードです。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gae3ce1d7385ca02a9f6c36768fa41c610)
