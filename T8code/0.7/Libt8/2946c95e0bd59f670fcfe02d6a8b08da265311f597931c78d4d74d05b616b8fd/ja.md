```
t8_stash_destroy(pstash)
```

スタッシュ構造体に関連するすべてのメモリを解放します。

# 引数

  * `pstash`:[in,out] 破棄されるスタッシュへのポインタ。関数呼び出し後、ポインタはNULLに設定されます。

### プロトタイプ

```c
void t8_stash_destroy (t8_stash_t *pstash);
```
