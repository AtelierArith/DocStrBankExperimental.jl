```
sc_io_sink_align(sink, bytes_align)
```

ゼロを書き込むことによって、シンクをバイト境界に整列させます。

### パラメータ

  * `sink`:[in,out] 整列させるシンクオブジェクト。
  * `bytes_align`:[in] バイト境界。

### 戻り値

成功した場合は0、エラーの場合は非ゼロ。

### プロトタイプ

```c
int sc_io_sink_align (sc_io_sink_t * sink, size_t bytes_align);
```
