```
t8_geometry_tree_negative_volume(cmesh, gtreeid)
```

ツリーが負の体積を持っているかどうかを確認します

# 引数

  * `cmesh`:[in] 確認するcmesh
  * `gtreeid`:[in] ツリーのグローバルID

# 戻り値

IDがgtreeidのツリーが負の体積を持っている場合はTrue。そうでない場合はFalse。

### プロトタイプ

```c
int t8_geometry_tree_negative_volume (const t8_cmesh_t cmesh, const t8_gloidx_t gtreeid);
```
