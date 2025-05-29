```
sc_array_memory_used(array, is_dynamic)
```

配列が使用しているメモリを計算します。

### パラメータ

  * `array`:[in] 配列。
  * `is_dynamic`:[in] [`sc_array_new`](@ref) で作成された場合は true、[`sc_array_init`](@ref) で初期化された場合は false。

### 戻り値

バイト単位での使用メモリ。

### プロトタイプ

```c
size_t sc_array_memory_used (sc_array_t * array, int is_dynamic);
```
