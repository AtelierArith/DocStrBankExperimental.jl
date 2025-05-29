```
p4est_ghost_exchange_data(p4est_, ghost, ghost_data)
```

ゴーストのローカル四分木のデータを他のプロセッサに転送します。これは、`p4est`->data*sizeが0の場合はポインタ変数自体、または`p4est`->data*sizeが正の場合は参照されたメモリフィールドの内容です。

### パラメータ

  * `p4est`:[in] 参照に使用されるフォレスト。
  * `ghost`:[in] 参照に使用されるゴーストレイヤー。
  * `ghost_data`:[in,out] すべてのゴースト四分木のために事前に割り当てられた連続データ。`p4est`->data*sizeが0の場合、各々のために少なくともsizeof (void *)バイトを保持する必要があります。それ以外の場合は、`p4est`->data*sizeごとに保持する必要があります。

### プロトタイプ

```c
void p4est_ghost_exchange_data (p4est_t * p4est, p4est_ghost_t * ghost, void *ghost_data);
```
