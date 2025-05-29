```
C_iio_buffer_refill(buffer)
```

ハードウェアからさらにサンプルを取得します。

# パラメータ

  * `buffer::Ptr{iio_buffer}` : iio_buffer 構造体へのポインタ

# 戻り値

  * 成功した場合、読み取られたバイト数が返されます
  * エラーの場合、負の errno コードが返されます

# 注意

入力バッファにのみ有効です

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#gac999e5244b5a2cbbca5ecaef8303a4ff)
