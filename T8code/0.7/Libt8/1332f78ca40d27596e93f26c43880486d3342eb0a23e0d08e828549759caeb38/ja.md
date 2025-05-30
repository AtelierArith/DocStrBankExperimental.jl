```
t8_cmesh_trees_get_attribute(trees, ltree_id, package_id, key, size, is_ghost)
```

ツリーに保存されている属性を返します。

# 引数

  * `trees`:[in] ツリー構造体。
  * `ltree_id`:[in] 属性が問い合わせられるツリーのローカルID。
  * `package_id`:[in] 属性のパッケージ識別子。
  * `key`:[in] 同じパッケージ識別子内のすべての属性の中での属性のキー。
  * `size`:[out] NULLでない場合、属性のサイズ（バイト単位）がここに格納されます。
  * `is_ghost`:[in] trueの場合、*ltree_id*はゴーストのlocal_idとして解釈されます。

# 戻り値

問い合わせられた属性へのポインタ、属性が存在しない場合はNULL。

### プロトタイプ

```c
void * t8_cmesh_trees_get_attribute (const t8_cmesh_trees_t trees, const t8_locidx_t ltree_id, const int package_id, const int key, size_t *size, int is_ghost);
```
