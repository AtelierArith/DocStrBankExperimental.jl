```
t8_geometry_tree_negative_volume(cmesh, gtreeid)
```

ツリーが負の体積を持っているかどうかを確認します

# 引数

  * `cmesh`:[in] チェックするcmesh
  * `gtreeid`:[in] ツリーのグローバルID

# 戻り値

ツリーのID gtreeid が負の体積を持っている場合は True。そうでない場合は False。

### プロトタイプ

```c
int t8_geometry_tree_negative_volume (const t8_cmesh_t cmesh, const t8_gloidx_t gtreeid);
```
