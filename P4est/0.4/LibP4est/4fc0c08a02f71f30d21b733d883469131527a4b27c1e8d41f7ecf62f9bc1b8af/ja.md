```
p4est_connectivity_new_copy(num_vertices, num_trees, num_corners, vertices, ttv, ttt, ttf, ttc, coff, ctt, ctc)
```

接続構造体を割り当て、定数からポピュレートします。属性フィールドはNULLに初期化されます。

### パラメータ

  * `num_vertices`:[in] 総頂点数（すなわち、幾何学的ポイント）。
  * `num_trees`:[in] 森の中の木の数。
  * `num_corners`:[in] 木を接続するコーナーの数。
  * `coff`:[in] コーナーから木へのオフセット（num*corners + 1の値）。これは常にNULLであってはならず、トリビアルな場合は単に0のp4est*topix値へのポインタです。

### 戻り値

接続の有効性がチェックされます。

### プロトタイプ

```c
p4est_connectivity_t *p4est_connectivity_new_copy (p4est_topidx_t num_vertices, p4est_topidx_t num_trees, p4est_topidx_t num_corners, const double *vertices, const p4est_topidx_t * ttv, const p4est_topidx_t * ttt, const int8_t * ttf, const p4est_topidx_t * ttc, const p4est_topidx_t * coff, const p4est_topidx_t * ctt, const int8_t * ctc);
```
