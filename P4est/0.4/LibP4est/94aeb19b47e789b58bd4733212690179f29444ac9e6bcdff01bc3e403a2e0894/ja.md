```
p8est_find_corner_transform(connectivity, itree, icorner, ci)
```

コーナー隣接情報を含む配列を埋めます。

### パラメータ

  * `itree`:[in] 元の木の番号。
  * `icorner`:[in] 元のコーナーの番号。
  * `ci`:[in,out] 初期化された配列を持つ `p8est_corner_info_t` 構造体。

### プロトタイプ

```c
void p8est_find_corner_transform (p8est_connectivity_t * connectivity, p4est_topidx_t itree, int icorner, p8est_corner_info_t * ci);
```
