```
t8_cmesh_trees_add_ghost_attribute(trees, attr, local_ghost_id, ghosts_inserted, index)
```

スタッシュから次のゴースト属性をキャラクタポインタ構造の正しい位置に追加します。スタッシュから作成されるため、すべての属性は部分0に追加されます。次の属性オフセットはすでに更新されます。

# 引数

  * `trees`:[in,out] キャラクタ配列が更新されるツリー構造。
  * `attr`:[in] 追加されるスタッシュ属性。
  * `local_ghost_id`:[in] ローカルゴーストID。
  * `ghosts_inserted`:[in] すでに挿入されたゴーストの数、これにより末尾を上書きしないようにします。
  * `index`:[in] 追加される属性の属性インデックス。

### プロトタイプ

```c
void t8_cmesh_trees_add_ghost_attribute (const t8_cmesh_trees_t trees, const t8_stash_attribute_struct_t *attr, t8_locidx_t local_ghost_id, t8_locidx_t ghosts_inserted, size_t index);
```
