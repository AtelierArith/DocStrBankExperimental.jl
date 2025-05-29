```
sc_hash_new(hash_fn, equal_fn, user_data, allocator)
```

新しいハッシュテーブルを作成します。ハッシュスロットの数は動的に選択されます。

### パラメータ

  * `hash_fn`:[in] ハッシュ値を計算する関数。
  * `equal_fn`:[in] 2つのオブジェクトの等価性をテストする関数。
  * `user_data`:[in] ハッシュ関数に渡されるユーザーデータ。
  * `allocator`:[in] [`sc_link_t`](@ref) のためのメモリアロケータ、NULLでも可。

### プロトタイプ

```c
sc_hash_t *sc_hash_new (sc_hash_function_t hash_fn, sc_equal_function_t equal_fn, void *user_data, sc_mempool_t * allocator);
```
