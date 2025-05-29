```
sc_hash_array_new(elem_size, hash_fn, equal_fn, user_data)
```

新しいハッシュ配列を作成します。

### パラメータ

  * `elem_size`:[in] 配列の1要素のサイズ（バイト単位）。
  * `hash_fn`:[in] ハッシュ値を計算する関数。
  * `equal_fn`:[in] 2つのオブジェクトの等価性をテストする関数。

### プロトタイプ

```c
sc_hash_array_t *sc_hash_array_new (size_t elem_size, sc_hash_function_t hash_fn, sc_equal_function_t equal_fn, void *user_data);
```
