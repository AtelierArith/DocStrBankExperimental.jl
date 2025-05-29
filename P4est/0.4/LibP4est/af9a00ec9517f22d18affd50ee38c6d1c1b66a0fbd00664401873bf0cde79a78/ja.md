```
sc_io_source_read_mirror(source, data, bytes_avail, bytes_out)
```

ソースのミラーからデータを読み取ります。 [`sc_io_source_read`](@ref) と同じ動作です。

### パラメータ

  * `source`:[in,out] ミラーデータを読み取るソースオブジェクト。

### 戻り値

成功時は0、エラー時は非ゼロ。

### プロトタイプ

```c
int sc_io_source_read_mirror (sc_io_source_t * source, void *data, size_t bytes_avail, size_t * bytes_out);
```
