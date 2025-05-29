```
sc_hash_unlink(hash)
```

ハッシュ要素をすべてリンク解除し、メモリプールに戻しません。

アロケータが所有されていない場合、これは[`sc_hash_truncate`](@ref)よりも速く実行されますが、メモリリークの可能性があるため危険です。

### パラメータ

  * `hash`:[in,out] リンク解除されるハッシュ構造体。

### プロトタイプ

```c
void sc_hash_unlink (sc_hash_t * hash);
```
