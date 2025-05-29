```
t8_cmesh_get_tree_geom_hash(cmesh, gtreeid)
```

cmesh内のツリーに保存されているジオメトリのハッシュを取得します。

# 引数

  * `cmesh`:[in] コミットされたcmesh。
  * `gtreeid`:[in] *cmesh*内のグローバルツリー。

# 戻り値

ツリーのジオメトリのハッシュ、またはジオメトリが1つだけ存在する場合、そのハッシュ。

### プロトタイプ

```c
size_t t8_cmesh_get_tree_geom_hash (t8_cmesh_t cmesh, t8_gloidx_t gtreeid);
```
