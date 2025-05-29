```
t8_cmesh_set_tree_geometry(cmesh, gtreeid, geom)
```

ツリーのジオメトリを設定し、このツリーに使用するジオメトリを指定します。

# 引数

  * `cmesh`:[in] コミットされていないcmesh。
  * `gtreeid`:[in] *cmesh*内のグローバルツリーID。
  * `geom`:[in] このツリーに使用するジオメトリ。t8*cmesh*get*tree*geometryも参照してください。

### プロトタイプ

```c
void t8_cmesh_set_tree_geometry (t8_cmesh_t cmesh, t8_gloidx_t gtreeid, const t8_geometry_c *geom);
```
