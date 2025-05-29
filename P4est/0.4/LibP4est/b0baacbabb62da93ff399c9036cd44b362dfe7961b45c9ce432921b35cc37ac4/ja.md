```
sc_io_source_read(source, data, bytes_avail, bytes_out)
```

ソースからデータを読み取ります。内部カウンタ source->bytes*in と source->bytes*out が更新されます。データは、データバッファに十分な余裕がなくなるか、ソースが空になるまで読み取られます。内部で既に読み取られたデータが、次の呼び出しのためにソースオブジェクトに残る可能性があります。[`sc_io_source_complete`](@ref) を呼び出し、その戻り値を確認して確認してください。bytes*out が NULL で、bytes*avail 未満のバイトが読み取られた場合はエラーを返します。

### パラメータ

  * `source`:[in,out] 読み取るソースオブジェクト。
  * `data`:[in] シンクから読み取るためのデータバッファ。NULL の場合、出力データは破棄されます。
  * `bytes_avail`:[in] データバッファ内の利用可能なバイト数。
  * `bytes_out`:[in,out] NULL でない場合、データバッファに読み取られたバイト数。そうでない場合、正確に bytes_avail を読み取る必要があります。

### 戻り値

成功時は 0、エラー時は非ゼロを返します。

### プロトタイプ

```c
int sc_io_source_read (sc_io_source_t * source, void *data, size_t bytes_avail, size_t * bytes_out);
```
