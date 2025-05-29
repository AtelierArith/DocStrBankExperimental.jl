```
sc_io_source_align(source, bytes_align)
```

ソースをバイト境界に揃えるためにスキップします。

### パラメータ

  * `source`:[in,out] 揃えるソースオブジェクト。
  * `bytes_align`:[in] バイト境界。

### 戻り値

成功時は0、エラー時は非ゼロ。

### プロトタイプ

```c
int sc_io_source_align (sc_io_source_t * source, size_t bytes_align);
```
