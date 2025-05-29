```
sc_list_new(allocator)
```

新しい空のリンクリストを割り当てます。

### パラメータ

  * `allocator`:[in] [`sc_link_t`](@ref) のメモリアロケータ、NULLの場合は内部アロケータが作成されます。

### 戻り値

新しく割り当てられた空のリストオブジェクトへのポインタ。

### プロトタイプ

```c
sc_list_t *sc_list_new (sc_mempool_t * allocator);
```
