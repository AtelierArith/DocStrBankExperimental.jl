```
C_iio_device_attr_write_raw(device, attr, value)
```

指定されたデバイス固有の属性の値を設定します。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `attr::String`            : 属性の名前に対応する NULL 終端文字列
  * `value::Ptr{Cvoid}`       : 書き込むデータへのポインタ
  * `size::Csize_t`           : 書き込むバイト数

# 戻り値

  * 成功した場合、書き込まれたバイト数
  * エラーの場合、負の errno コードが返されます

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga30829a67dcdffc902c4ba6801233e79a)
