```
t8_geometry_evaluate(cmesh, gtreeid, ref_coords, num_coords, out_coords)
```

指定された参照点でツリーのジオメトリを評価します。

# 引数

  * `cmesh`:[in] cmesh
  * `gtreeid`:[in] ツリーのグローバルID
  * `ref_coords`:[in] ジオメトリを評価するための参照座標
  * `num_coords`:[in] 参照座標の数
  * `out_coords`:[out] 評価された座標

### プロトタイプ

```c
void t8_geometry_evaluate (t8_cmesh_t cmesh, t8_gloidx_t gtreeid, const double *ref_coords, const size_t num_coords, double *out_coords);
```
