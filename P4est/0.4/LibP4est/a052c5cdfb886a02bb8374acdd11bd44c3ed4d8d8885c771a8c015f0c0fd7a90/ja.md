```
p4est_find_corner_transform(connectivity, itree, icorner, ci)
```

コーナー隣接情報を含む配列を埋めます。

### パラメータ

  * `itree`:[in] 元の木の番号。
  * `icorner`:[in] 元のコーナーの番号。
  * `ci`:[in,out] 初期化された配列を持つ `p4est_corner_info_t` 構造体。

### プロトタイプ

```c
void p4est_find_corner_transform (p4est_connectivity_t * connectivity, p4est_topidx_t itree, int icorner, p4est_corner_info_t * ci);
```
