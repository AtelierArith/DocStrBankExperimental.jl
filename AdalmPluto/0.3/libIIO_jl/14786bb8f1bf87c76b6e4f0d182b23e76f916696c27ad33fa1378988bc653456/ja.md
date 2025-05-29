```
C_iio_buffer_foreach_sample()
```

これはプレースホルダーです。以下のドキュメントはCドキュメントのコピー/ペーストです。

バッファ内で見つかった各サンプルに対して、指定されたコールバックを呼び出します。

# パラメータ

  * buf : iio_buffer構造体へのポインタ
  * callback : 見つかった各サンプルに対して呼び出す関数へのポインタ
  * data : コールバックに渡されるユーザー指定のポインタ

# 戻り値

  * 処理されたバイト数。

# 注意

コールバックは4つの引数を受け取ります：

  * サンプルに対応するiio_channel構造体へのポインタ、
  * サンプル自体へのポインタ、
  * サンプルのバイト数、
  * `iio_buffer_foreach_sample`に渡されたユーザー指定のポインタ。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#ga810ec50155e82331b18ec71d3c507104)
