```
sc_hash_unlink_destroy(hash)
```

unlinkとdestroyと同じ効果がありますが、O(1)で実行されます。これは潜在的なメモリリークのため危険です。

### パラメータ

  * `hash`:[in] アンリンクされ破棄されるハッシュ構造体。

### プロトタイプ

```c
void sc_hash_unlink_destroy (sc_hash_t * hash);
```
