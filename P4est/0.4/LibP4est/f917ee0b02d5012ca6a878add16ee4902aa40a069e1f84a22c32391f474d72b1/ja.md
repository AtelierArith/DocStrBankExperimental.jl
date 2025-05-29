```
p4est_ghost_checksum(p4est_, ghost)
```

ゴーストレイヤーの並列チェックサムを計算します。

### パラメータ

  * `p4est`:[in] この `p4est` のMPI情報が使用されます。
  * `ghost`:[in] `p4est` から取得したゴーストレイヤー。

### 戻り値

ランク0の並列チェックサム、その他は0。

### プロトタイプ

```c
unsigned p4est_ghost_checksum (p4est_t * p4est, p4est_ghost_t * ghost);
```
