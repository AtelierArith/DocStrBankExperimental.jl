```
C_iio_device_attr_write_double(device, attr, value)
```

指定されたデバイス固有の属性の値を設定します。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `attr::String`            : 属性の名前に対応する NULL 終端文字列
  * `value::Float64`          : 属性に設定するダブル値

# 戻り値

  * 成功した場合、0 が返されます
  * エラーの場合、負の errno コードが返されます

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gacdaf529f12b46ba2a5290bbc590c8b9e)
