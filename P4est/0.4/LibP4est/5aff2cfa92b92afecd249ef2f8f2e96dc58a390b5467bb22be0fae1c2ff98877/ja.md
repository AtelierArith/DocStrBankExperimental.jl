```
p4est_ghost_exchange_custom_levels(p4est_, ghost, minlevel, maxlevel, data_size, mirror_data, ghost_data)
```

ローカルのクワドラントがゴーストであるデータを他のプロセッサに転送します。データサイズはすべてのクワドラントで同じであり、任意に選択できます。この関数は、転送を細分化レベルの範囲に制限します。レベル範囲外のクワドラントのメモリは解放されません。

### パラメータ

  * `p4est`:[in] 参照に使用されるフォレスト。
  * `ghost`:[in] 参照に使用されるゴーストレイヤー。
  * `minlevel`:[in] 交換される最大のクワッドのレベル。制限を設けない場合は <= 0 を使用します。
  * `maxlevel`:[in] 交換される最小のクワッドのレベル。制限を設けない場合は >= `P4EST_QMAXLEVEL` を使用します。
  * `data_size`:[in] 各クワドラントごとに転送するデータサイズ。
  * `mirror_data`:[in] ミラークワドラントごとのデータポインタを入力として。
  * `ghost_data`:[in,out] すべてのゴーストのために事前に割り当てられた連続データで、各ゴーストに対して少なくとも `data_size` を保持する必要があります。

### プロトタイプ

```c
void p4est_ghost_exchange_custom_levels (p4est_t * p4est, p4est_ghost_t * ghost, int minlevel, int maxlevel, size_t data_size, void **mirror_data, void *ghost_data);
```
