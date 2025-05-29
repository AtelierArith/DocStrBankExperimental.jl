```
C_iio_device_find_buffer_attr(device, name)
```

名前によってバッファ特有の属性を見つけようとします。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `name::String`            : 属性の名前に対応する NULL 終端の文字列

# 戻り値

  * 成功した場合、NULL 終端の文字列。
  * 失敗した場合、アサーションが有効な場合はエラーをスローします。
  * 失敗した場合、アサーションが無効な場合は空の文字列を返します。

# 注意

この関数は属性の存在を検出するのに役立ちます。また、動的に割り当てられた文字列から静的文字列へのポインタとして属性の名前を取得するためにも使用できます。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga58baa15da06b2d497fb0334f35264240)
