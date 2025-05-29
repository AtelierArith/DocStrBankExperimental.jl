```
sc_list_memory_used(list, is_dynamic)
```

リストによって使用される総メモリを計算します。

### パラメータ

  * `list`:[in] リスト。
  * `is_dynamic`:[in] [`sc_list_new`](@ref) で作成された場合は true、[`sc_list_init`](@ref) で初期化された場合は false。

### 戻り値

バイト単位で使用されるメモリ。

### プロトタイプ

```c
size_t sc_list_memory_used (sc_list_t * list, int is_dynamic);
```
