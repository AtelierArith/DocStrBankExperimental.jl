```
t8_cmesh_trees_init_attributes(trees, ltree_id, num_attributes, attr_bytes)
```

1つの木に対して、ツリー構造内の属性の数を設定し、この木のすべての属性の合計サイズを一時的に保存します。この一時的な値は、t8*cmesh*trees*finish*partで使用されます。

# 引数

  * `trees`:[in,out] 更新されるツリー構造。
  * `ltree_id`:[in] *trees*内の1つの木のローカルID。
  * `num_attributes`:[in] この木の属性の数。
  * `attr_bytes`:[in] この木のすべての属性の合計バイト数。

### プロトタイプ

```c
void t8_cmesh_trees_init_attributes (t8_cmesh_trees_t trees, t8_locidx_t ltree_id, size_t num_attributes, size_t attr_bytes);
```
