```
C_iio_device_buffer_attr_write(device, attr, value)
```

指定されたバッファ固有の属性の値を設定します。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `attr::String`            : 属性の名前に対応する NULL 終端の文字列
  * `value::String`           : 属性に設定するための NULL 終端の文字列

# 戻り値

  * 成功した場合、書き込まれたバイト数
  * エラーの場合、負の errno コードが返される

# 注意

`iio_device_buffer_attr_write` に "attr" 引数として NULL を渡すことで、デバイスのすべての属性を書き込むことが可能になりました。

バッファは、iio_device 構造体に表示される順序で、各属性ごとに 1 つのデータブロックを含む必要があります。

1 つのブロックの最初の 4 バイトは、ネットワークオーダーの 32 ビット符号付き値に対応します。負の場合、属性は書き込まれず、正の場合は書き込むデータの長さに対応します。その場合、ブロックの残りにはデータが含まれている必要があります。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#ga8a12066003b7ef442e95bfbc22b4370b)
