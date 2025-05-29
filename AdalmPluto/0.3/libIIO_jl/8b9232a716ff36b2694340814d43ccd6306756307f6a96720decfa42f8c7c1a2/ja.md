```
C_iio_buffer_get_poll_fd(buffer)
```

ポーラブルファイルディスクリプタを取得します。

`iio_buffer_refill()` または `iio_buffer_push()` を呼び出すことができるときがわかります。

# パラメータ

  * `buffer::Ptr{iio_buffer}` : iio_buffer 構造体へのポインタ

# 戻り値

  * 成功した場合、有効なファイルディスクリプタ
  * エラーの場合、負の errno コードが返されます

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#ga2ae96ee9f0748e55dfad996d6e9883f2)
