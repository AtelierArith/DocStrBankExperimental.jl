```
sc_io_sink_write(sink, data, bytes_avail)
```

シンクにデータを書き込みます。データはバッファリングされ、後の呼び出しでシンクされる場合があります。内部カウンタ sink->bytes*in と sink->bytes*out が更新されます。

### パラメータ

  * `sink`:[in,out] 書き込むシンクオブジェクト。
  * `data`:[in] シンクに渡されるデータ。
  * `bytes_avail`:[in] 渡されるデータバイト数。

### 戻り値

成功時は0、エラー時は非ゼロ。

### プロトタイプ

```c
int sc_io_sink_write (sc_io_sink_t * sink, const void *data, size_t bytes_avail);
```
