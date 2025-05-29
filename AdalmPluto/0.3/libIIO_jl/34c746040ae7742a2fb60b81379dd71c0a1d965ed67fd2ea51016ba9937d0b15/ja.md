```
C_iio_channel_attr_write(channel, attr, value)
```

指定されたチャネル固有の属性の値を設定します。

# パラメータ

  * `channel::Ptr{iio_channel}` : iio_channel 構造体へのポインタ
  * `attr::String` : 属性の名前に対応する NULL 終端の文字列
  * `value::String` : 属性を設定するための NULL 終端の文字列

# 戻り値

  * 成功した場合、書き込まれたバイト数
  * エラーの場合、負の errno コードが返される

# 注意

`iio_channel_attr_write` に "attr" 引数として NULL を渡すことで、チャネルのすべての属性を書き込むことが可能になりました。

バッファは、iio_channel 構造体に表示される順序で、チャネルの各属性ごとに 1 ブロックのデータを含む必要があります。

1 ブロックの最初の 4 バイトは、ネットワークオーダーの 32 ビット符号付き値に対応します。負の場合、属性は書き込まれず、正の場合は書き込むデータの長さに対応します。その場合、ブロックの残りにはデータが含まれている必要があります。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga35c76ce5fcae4c551b7c78d648665a41)
