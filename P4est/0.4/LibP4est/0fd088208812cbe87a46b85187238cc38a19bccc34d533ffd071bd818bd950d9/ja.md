```
sc_io_source_destroy(source)
```

データソースを解放します。[`sc_io_source_complete`](@ref)を呼び出し、エラーを返さないことを要求します。これは、読み取りに渡されていないバッファリングされたデータが破棄されるのを避けるためです。

### パラメータ

  * `source`:[in,out] 解放するソースオブジェクト。

### 戻り値

成功した場合は0。エラーが発生した場合やis_completeが1を返す場合は非ゼロ。

### プロトタイプ

```c
int sc_io_source_destroy (sc_io_source_t * source);
```
