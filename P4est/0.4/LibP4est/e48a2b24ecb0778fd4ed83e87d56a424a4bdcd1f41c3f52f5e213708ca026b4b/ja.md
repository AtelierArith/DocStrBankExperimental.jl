```
sc_io_source_complete(source, bytes_in, bytes_out)
```

ソースからバッファリングされたすべてのデータが読み取られたかどうかを判断します。もし SC*IO*ERROR*AGAIN を返す場合、別の [`sc*io*source*read`](@ref) が必要です。呼び出しがエラーを返さない場合、内部カウンタ source->bytes*in と source->bytes*out が要求された場合に呼び出し元に返され、0 にリセットされます。ソースの内部状態はそれ以外は変更されません。ここから先もソースからの読み取りを続けることは合法です。

### パラメータ

  * `source`:[in,out] 読み取るソースオブジェクト。
  * `bytes_in`:[in,out] NULL でなく、true が返された場合、ソースされたデータの合計サイズ。
  * `bytes_out`:[in,out] NULL でなく、true が返された場合、source_read によって出力された合計バイト数。

### 戻り値

バッファリングされたデータが残っている場合は SC*IO*ERROR*AGAIN を返します。それ以外の場合は ERROR*NONE を返し、カウンタをリセットします。

### プロトタイプ

```c
int sc_io_source_complete (sc_io_source_t * source, size_t * bytes_in, size_t * bytes_out);
```
