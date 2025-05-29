```
sc_list_init(list, allocator)
```

外部リンクアロケータを使用してリストオブジェクトを初期化します。

### パラメータ

  * `list`:[in,out] 初期化されるリスト構造体。
  * `allocator`:[in] すでに存在する必要がある[`sc_link_t`](@ref)のための外部メモリアロケータ。

### プロトタイプ

```c
void sc_list_init (sc_list_t * list, sc_mempool_t * allocator);
```
