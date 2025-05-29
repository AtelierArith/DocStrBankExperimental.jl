```
t8_cmesh_trees_ghost_attribute_size(ghost)
```

指定されたゴーストに保存されているすべての属性の合計サイズを返します。

# 引数

  * `ghost`:[in] ゴースト構造体。

# 戻り値

*ghost* の属性の合計サイズ（バイト単位）。

### プロトタイプ

```c
size_t t8_cmesh_trees_ghost_attribute_size (t8_cghost_t ghost);
```
