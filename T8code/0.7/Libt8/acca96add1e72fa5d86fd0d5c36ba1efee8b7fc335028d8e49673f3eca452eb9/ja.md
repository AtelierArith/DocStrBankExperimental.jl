```
t8_forest_set_ghost(forest, do_ghost, ghost_type)
```

ゴースト要素の層の作成を有効または無効にします。デフォルトではゴーストは作成されません。

# 引数

  * `forest`:[in] 森。
  * `do_ghost`:[in] ゼロ以外の場合、ゴースト層が作成されます。
  * `ghost_type`:[in] どの隣接要素がゴースト要素としてカウントされるかを制御します。現在は T8*GHOST*FACES のみがサポートされています。この値は *do_ghost* = 0 の場合は無視されます。

### プロトタイプ

```c
void t8_forest_set_ghost (t8_forest_t forest, int do_ghost, t8_ghost_type_t ghost_type);
```
