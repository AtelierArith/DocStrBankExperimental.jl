```
C_iio_device_buffer_attr_write_double(device, attr, value)
```

指定されたバッファ固有の属性の値を設定します。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `attr::String`            : 属性の名前に対応する NULL 終端文字列
  * `value::Float64`          : 属性に設定するダブル値

# 戻り値

  * 成功した場合、0 が返されます
  * エラーの場合、負の errno コードが返されます

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga10d47af8de4ad1f9dc4b63ce0aa0ff7d)
