```
sc_io_source_activate_mirror(source)
```

読み取られたデータをミラー（すなわち、保存）するバッファをアクティブにします。

### パラメータ

  * `source`:[in,out] ミラーをアクティブにするソースオブジェクト。

### 戻り値

成功時は0、エラー時は非ゼロ。

### プロトタイプ

```c
int sc_io_source_activate_mirror (sc_io_source_t * source);
```
