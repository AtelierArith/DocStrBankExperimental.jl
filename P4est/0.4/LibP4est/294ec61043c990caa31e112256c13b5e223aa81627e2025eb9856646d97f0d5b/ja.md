```
p8est_ghost_exchange_data(p8est_, ghost, ghost_data)
```

ゴーストのローカル区画のデータを他のプロセッサに転送します。これは、`p8est`->data*sizeが0の場合はポインタ変数自体、または`p8est`->data*sizeが正の場合は参照されたメモリフィールドの内容です。

### パラメータ

  * `p8est`:[in] 参照に使用されるフォレスト。
  * `ghost`:[in] 参照に使用されるゴーストレイヤー。
  * `ghost_data`:[in,out] すべてのゴースト区画のために事前に割り当てられた連続データ。`p8est`->data*sizeが0の場合、各区画のために少なくともsizeof (void *)バイトを保持する必要があります。それ以外の場合は、`p8est`->data*sizeごとに保持する必要があります。

### プロトタイプ

```c
void p8est_ghost_exchange_data (p8est_t * p8est, p8est_ghost_t * ghost, void *ghost_data);
```
