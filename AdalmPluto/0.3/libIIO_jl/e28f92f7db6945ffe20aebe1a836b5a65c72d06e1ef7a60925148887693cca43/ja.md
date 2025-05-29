```
C_iio_device_set_kernel_buffers_count(device, nb_buffers)
```

デバイスのカーネルバッファの数を設定します。

この関数は、カーネル側のバッファの数を変更することを可能にします。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `nb_buffers::UInt32`      : バッファの数

# 戻り値

  * 成功した場合、0 が返されます
  * エラーの場合、負の errno コードが返されます

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga8ad2357c4caf7afc778060a08e6e2209)
