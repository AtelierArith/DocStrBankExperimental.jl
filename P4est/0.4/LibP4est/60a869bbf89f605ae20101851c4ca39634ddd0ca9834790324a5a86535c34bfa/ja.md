```
p4est_ghost_memory_used(ghost)
```

ゴースト層のメモリ使用量を計算します。

### パラメータ

  * `ghost`:[in] ゴースト層構造体。

### 戻り値

バイト単位の使用メモリ。

### プロトタイプ

```c
size_t p4est_ghost_memory_used (p4est_ghost_t * ghost);
```
