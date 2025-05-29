```
t8_cmesh_trees_is_face_consistent(cmesh, trees)
```

ツリー構造の面接続が一貫しているかどうかを確認します。つまり、tree1が面iでttfエントリを持つtree2を隣接としてリストしている場合（または、面jの場合）、tree2は面jでttfエントリを持つtree1を隣接としてリストしなければなりません（または、面iの場合）。

# 引数

  * `cmesh`:[in] チェックされるcmesh構造。
  * `trees`:[in] cmeshのツリー構造。

# 戻り値

面接続が一貫している場合はTrue、一貫していない場合はFalse。

### プロトタイプ

```c
int t8_cmesh_trees_is_face_consistent (t8_cmesh_t cmesh, t8_cmesh_trees_t trees);
```
