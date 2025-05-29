```
p8est_ghost_memory_used(ghost)
```

ゴーストレイヤーのメモリ使用量を計算します。

### パラメータ

  * `ghost`:[in] ゴーストレイヤー構造体。

### 戻り値

バイト単位の使用メモリ。

### プロトタイプ

```c
size_t p8est_ghost_memory_used (p8est_ghost_t * ghost);
```
