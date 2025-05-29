```
t8_cmesh_trees_get_part(trees, proc)
```

指定されたツリー配列の一部を返します。

# 引数

  * `trees`:[in] 問い合わせるツリー配列
  * `proc`:[in] 返される部分を指定するインデックス。

# 戻り値

*trees* の部分番号 *proc*。

### プロトタイプ

```c
t8_part_tree_t t8_cmesh_trees_get_part (const t8_cmesh_trees_t trees, const int proc);
```
