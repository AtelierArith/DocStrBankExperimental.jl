```
t8_sc_array_index_locidx(array, it)
```

[`t8_locidx_t`](@ref)でインデックスされた配列要素へのポインタを返します。

# 引数

  * `index`:[in] は [0]..[elem_count-1] の範囲内である必要があります。

# 戻り値

配列 *array* のエントリ *it* を指す void *。

### プロトタイプ

```c
void * t8_sc_array_index_locidx (const sc_array_t *array, const t8_locidx_t it);
```
