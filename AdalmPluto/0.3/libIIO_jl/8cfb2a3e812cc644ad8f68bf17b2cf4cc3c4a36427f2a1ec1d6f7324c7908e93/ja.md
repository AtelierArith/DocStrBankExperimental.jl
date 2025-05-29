```
C_iio_buffer_set_blocking_mode(buffer, blocking)
```

`iio_buffer_refill()` と `iio_buffer_push()` をブロッキングまたはノンブロッキングにします。

この関数が `blocking == false` で呼び出された後、`iio_buffer_refill()` と `iio_buffer_push()` はデータが準備されていない場合に -EAGAIN を返します。デフォルトではデバイスはブロッキングです。

# パラメータ

  * `buffer::Ptr{iio_buffer}` : iio_buffer 構造体へのポインタ
  * `blocking::Bool` : バッファ API がブロッキングであるべきなら true、そうでなければ false

# 戻り値

  * 成功した場合、0
  * エラーの場合、負の errno コードが返されます

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Buffer.html#gadf834d825ece149886283bcb8c2a5466)
