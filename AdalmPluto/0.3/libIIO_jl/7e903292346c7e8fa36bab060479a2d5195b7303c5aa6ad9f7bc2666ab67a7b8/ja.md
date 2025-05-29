```
C_iio_buffer_push_partial(buffer, sample_count)
```

ハードウェアに指定された数のサンプルを送信します。

# パラメータ

  * `buffer::Ptr{iio_buffer}` : iio_buffer 構造体へのポインタ
  * `samples_count::UInt` : 提出するサンプルの数

# 戻り値

  * 成功した場合、書き込まれたバイト数が返されます
  * エラーの場合、負の errno コードが返されます

# 注意

出力バッファにのみ有効です

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#ga367b7368532aebb35a0d56bccc550570)
