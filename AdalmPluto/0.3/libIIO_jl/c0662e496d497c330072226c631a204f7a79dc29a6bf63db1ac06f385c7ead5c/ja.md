```
C_iio_channel_attr_read(channel, attr)
```

指定されたチャネル固有の属性の内容を読み取ります。

# パラメータ

  * `channel::Ptr{iio_channel}` : iio_channel 構造体へのポインタ
  * `attr::String` : 属性の名前に対応する NULL 終端文字列

# 戻り値

  * 成功した場合、`(nbytes, value::String)` が返され、nbytes は値の文字列の長さです。
  * エラーの場合、`(errno, "")` が返され、errno は負のエラーコードです。
  * すべての属性が読み取られる場合、上記の値の配列が返されます。

文字列は、変換が余分な NULL 文字を切り捨てるため、返されるバイト数よりも短い場合があります。

# 注意

`iio_channel_attr_read` に "attr" 引数として NULL（Julia ラッパー内で空文字列に置き換えられます）を渡すことで、チャネルのすべての属性を読み取ることが可能になりました。

バッファは、iio_channel 構造体に表示される順序で、チャネルの各属性ごとに 1 ブロックのデータで満たされます。

1 ブロックの最初の 4 バイトは、ネットワークオーダーの 32 ビット符号付き値に対応します。負の場合は、属性を読み取る際に返された errno コードに対応し、正の場合は読み取ったデータの長さに対応します。その場合、ブロックの残りにはデータが含まれます。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga2c2ca5696d1341067051eb390d5014ae)
