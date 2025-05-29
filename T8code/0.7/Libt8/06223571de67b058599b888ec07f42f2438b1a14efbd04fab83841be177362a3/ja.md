```
t8_offset_first_tree_to_entry(first_tree, shared)
```

プロセスの最初のローカルツリーのグローバルツリーIDと、それが共有されているかどうかのフラグを考慮して、オフセット配列のエントリを計算します。このエントリは、共有されていない場合は `first_tree` であり、共有されている場合は `-first_tree - 1` です。

# 引数

  * `first_tree`:[in] プロセスの最初のツリーのグローバルツリーID。
  * `shared`:[in] *first_tree* が小さいランクと共有されていない場合は 0、共有されている場合は 1。

# 戻り値

オフセット配列内のプロセスを表すエントリ。*shared* が 0 の場合は *first_tree* - *shared* が 0 でない場合は `-first_tree - 1`。

### プロトタイプ

```c
t8_gloidx_t t8_offset_first_tree_to_entry (const t8_gloidx_t first_tree, const int shared);
```
