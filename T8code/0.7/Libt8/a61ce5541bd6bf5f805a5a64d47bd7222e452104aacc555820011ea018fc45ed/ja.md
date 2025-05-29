```
t8_cmesh_trees_set_all_boundary(cmesh, trees)
```

すべてのローカルツリーとゴーストの隣接フィールドを境界に設定します。

# 引数

  * `cmesh,`:[in,out] 関連するcmesh。
  * `trees,`:[in,out] ツリー構造。ツリーtの面fは、面隣接が面fでtである場合、境界としてカウントされます。

### プロトタイプ

```c
void t8_cmesh_trees_set_all_boundary (t8_cmesh_t cmesh, t8_cmesh_trees_t trees);
```
