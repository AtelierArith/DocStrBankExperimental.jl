```
t8_geometry_jacobian(cmesh, gtreeid, ref_coords, num_coords, jacobian)
```

指定された参照点での木のヤコビアンを評価します。

# 引数

  * `cmesh`:[in] cmesh
  * `gtreeid`:[in] 木のグローバルID
  * `ref_coords`:[in] ヤコビアンを評価する参照座標
  * `num_coords`:[in] 参照座標の数
  * `jacobian`:[out] 参照座標でのヤコビアン

### プロトタイプ

```c
void t8_geometry_jacobian (t8_cmesh_t cmesh, t8_gloidx_t gtreeid, const double *ref_coords, const size_t num_coords, double *jacobian);
```
