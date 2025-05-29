```
C_iio_buffer_push(buffer)
```

ハードウェアにサンプルを送信します。

# パラメータ

  * `buffer::Ptr{iio_buffer}` : iio_buffer 構造体へのポインタ

# 戻り値

  * 成功した場合、書き込まれたバイト数が返されます
  * エラーの場合、負の errno コードが返されます

# 注意

出力バッファにのみ有効です

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#gae7033c625d128667a56cf482aa3149bd)
