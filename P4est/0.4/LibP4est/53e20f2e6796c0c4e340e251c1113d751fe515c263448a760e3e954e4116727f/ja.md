```
p8est_connectivity_new_copy(num_vertices, num_trees, num_edges, num_corners, vertices, ttv, ttt, ttf, tte, eoff, ett, ete, ttc, coff, ctt, ctc)
```

接続構造体を割り当て、定数からポピュレートします。属性フィールドはNULLに初期化されます。

### パラメータ

  * `num_vertices`:[in] 総頂点数（すなわち、幾何学的ポイント）。
  * `num_trees`:[in] 森の中の木の数。
  * `num_edges`:[in] 木を接続するエッジの数。
  * `num_corners`:[in] 木を接続するコーナーの数。
  * `eoff`:[in] エッジから木へのオフセット（num*edges + 1の値）。これは常に非NULLでなければなりません；簡単な場合は、単にp4est*topixの値0へのポインタです。
  * `coff`:[in] コーナーから木へのオフセット（num*corners + 1の値）。これは常に非NULLでなければなりません；簡単な場合は、単にp4est*topixの値0へのポインタです。

### 戻り値

接続の有効性がチェックされます。

### プロトタイプ

```c
p8est_connectivity_t *p8est_connectivity_new_copy (p4est_topidx_t num_vertices, p4est_topidx_t num_trees, p4est_topidx_t num_edges, p4est_topidx_t num_corners, const double *vertices, const p4est_topidx_t * ttv, const p4est_topidx_t * ttt, const int8_t * ttf, const p4est_topidx_t * tte, const p4est_topidx_t * eoff, const p4est_topidx_t * ett, const int8_t * ete, const p4est_topidx_t * ttc, const p4est_topidx_t * coff, const p4est_topidx_t * ctt, const int8_t * ctc);
```
