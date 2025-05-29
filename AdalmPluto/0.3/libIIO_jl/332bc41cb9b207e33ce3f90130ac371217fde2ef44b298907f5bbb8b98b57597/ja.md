```
C_iio_device_buffer_attr_read(device, attr)
```

指定されたバッファ固有の属性の内容を読み取ります。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `attr::String`            : 属性の名前に対応する NULL 終端の文字列。空の文字列を渡すと、すべての属性が読み取られます。

# 戻り値

  * 成功した場合、(number*of*bytes, value::String) が返されます。ここで、バイト数は文字列の長さである必要があります。
  * エラーの場合、(errno, "") が返されます。ここで、errno は負のエラーコードです。
  * すべての属性が読み取られる場合、上記の値の配列が返されます。

文字列は、変換が余分なヌル文字をトリムするため、実際のバイト数よりも短くなる場合があります。

# 注意

`iio_device_buffer_attr_read` に "attr" 引数として NULL（Julia ラッパーで空の文字列に置き換えられます）を渡すことで、デバイスのすべての属性を読み取ることが可能になりました。

バッファは、iio_device 構造体に表示される順序で、バッファの各属性ごとに1つのデータブロックで満たされます。

1つのブロックの最初の4バイトは、ネットワークオーダーの32ビット符号付き値に対応します。負の場合は、属性を読み取る際に返された errno コードに対応し、正の場合は読み取ったデータの長さに対応します。その場合、ブロックの残りにはデータが含まれます。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gaa77d52bb9dea248cc3de682778a08a6f)
