```
p8est_ghost_exchange_custom(p8est_, ghost, data_size, mirror_data, ghost_data)
```

ローカルのクワドラントであるゴーストのデータを他のプロセッサに転送します。データサイズはすべてのクワドラントで同じであり、任意に選択できます。

### パラメータ

  * `p8est`:[in] 参照に使用されるフォレスト。
  * `ghost`:[in] 参照に使用されるゴーストレイヤー。
  * `data_size`:[in] 各クワドラントごとに転送するデータサイズ。
  * `mirror_data`:[in] 各ミラークワドラントごとのデータポインタ。
  * `ghost_data`:[in,out] すべてのゴーストのために事前に割り当てられた連続データで、各ゴーストに対して少なくとも `data_size` を保持する必要があります。

### プロトタイプ

```c
void p8est_ghost_exchange_custom (p8est_t * p8est, p8est_ghost_t * ghost, size_t data_size, void **mirror_data, void *ghost_data);
```
