```
t8_cmesh_get_tree_geometry(cmesh, gtreeid)
```

ツリーのジオメトリを取得します。

# 引数

  * `cmesh`:[in] cmesh。
  * `gtreeid`:[in] ジオメトリを返すべきツリーのグローバルツリーID。

# 戻り値

ツリーのジオメトリ。

### プロトタイプ

```c
const t8_geometry_c * t8_cmesh_get_tree_geometry (t8_cmesh_t cmesh, t8_gloidx_t gtreeid);
```
