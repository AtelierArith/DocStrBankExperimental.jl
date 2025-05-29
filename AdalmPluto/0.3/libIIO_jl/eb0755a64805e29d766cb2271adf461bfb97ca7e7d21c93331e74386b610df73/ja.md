```
C_iio_device_buffer_attr_read_longlong(device, attr)
```

指定されたバッファ固有の属性の内容を読み取ります。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `attr::String`            : 属性の名前に対応する NULL 終端の文字列

# 戻り値

  * 成功した場合、(0, value::Int64) が返されます。
  * エラーの場合、(errno, value::Int64) が返されます。ここで errno は負のエラーコードです。`value` は破棄する必要があります。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gae5b9be890edb372d3e30a14ce1c79874)
