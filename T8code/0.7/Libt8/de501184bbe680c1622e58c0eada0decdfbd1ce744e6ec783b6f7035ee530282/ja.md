```
t8_forest_ghost_remote_first_tree(forest, remote)
```

リモートランクの最初のローカルゴーストツリーを返します。

# 引数

  * `forest`:[in] ゴーストレイヤーが構築されたフォレスト。
  * `remote`:[in] *forest*内のゴーストレイヤーのリモートランク。

# 戻り値

*remote*のゴースト要素を格納する最初のゴーストツリーのゴーストツリーID。

### プロトタイプ

```c
t8_locidx_t t8_forest_ghost_remote_first_tree (t8_forest_t forest, int remote);
```
