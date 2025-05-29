```
C_iio_device_buffer_attr_read_double(device, attr)
```

指定されたバッファ固有の属性の内容を読み取ります。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `attr::String`            : 属性の名前に対応する NULL 終端文字列

# 戻り値

  * 成功した場合、(0, value::Float64) が返されます。
  * エラーの場合、(errno, value::Float64) が返されます。ここで errno は負のエラーコードです。`value` は破棄する必要があります。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga44952198b73ff6b0c0c0b53d3cd6d1bd)
