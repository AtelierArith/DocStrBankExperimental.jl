```
p8est_ghost_is_valid(p8est_, ghost)
```

上記のように、ゴースト構造が有効かどうかを調べます。ゴースト構造内で、配列 ghosts と mirrors が p8est*quadrant*compare*piggy の順序になっているかをテストします。ghosts と mirrors の四分木の piggy3 データメンバー内の local*num が昇順になっているか（ゴーストごとにランク内で昇順）をテストします。

[`p4est_locidx_t`](@ref) 配列が昇順になっているか（mirror*proc*mirrors はランク内で昇順）をテストします。

### パラメータ

  * `p8est`:[in] 森。
  * `ghost`:[in] ゴーストレイヤー構造。

### 戻り値

*ghost* が有効な場合は true

### プロトタイプ

```c
int p8est_ghost_is_valid (p8est_t * p8est, p8est_ghost_t * ghost);
```
