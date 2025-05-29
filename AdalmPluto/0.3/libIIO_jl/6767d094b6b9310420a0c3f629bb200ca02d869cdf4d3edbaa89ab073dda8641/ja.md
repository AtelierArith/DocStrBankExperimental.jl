```
C_iio_device_attr_write_longlong(device, attr, value)
```

指定されたデバイス固有の属性の値を設定します。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `attr::String`            : 属性の名前に対応する NULL 終端文字列
  * `value::Int64`            : 属性に設定するための long long 値

# 戻り値

  * 成功した場合、0 が返されます
  * エラーの場合、負の errno コードが返されます

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga3fcba684f6b07d3f6295759bb788c4d2)
