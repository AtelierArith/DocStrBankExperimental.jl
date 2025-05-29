```
t8_forest_ghost_get_tree_elements(forest, lghost_tree)
```

ゴーストツリーのゴースト要素配列へのポインタを取得します。

# 引数

  * `forest`:[in] 森。ゴースト層が存在する必要があります。
  * `lghost_tree`:[in] ゴーストツリーのゴーストツリーID。

# 戻り値

ツリーのゴースト要素の配列へのポインタ。*forest*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_element_array_t * t8_forest_ghost_get_tree_elements (const t8_forest_t forest, const t8_locidx_t lghost_tree);
```
