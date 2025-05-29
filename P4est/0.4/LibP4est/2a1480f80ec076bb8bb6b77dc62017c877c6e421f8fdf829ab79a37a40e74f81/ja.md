```
p8est_ghost_checksum(p8est_, ghost)
```

ゴーストレイヤの並列チェックサムを計算します。

### パラメータ

  * `p8est`:[in] この `p8est` のMPI情報が使用されます。
  * `ghost`:[in] `p8est` から取得したゴーストレイヤ。

### 戻り値

ランク0の並列チェックサム、その他は0。

### プロトタイプ

```c
unsigned p8est_ghost_checksum (p8est_t * p8est, p8est_ghost_t * ghost);
```
