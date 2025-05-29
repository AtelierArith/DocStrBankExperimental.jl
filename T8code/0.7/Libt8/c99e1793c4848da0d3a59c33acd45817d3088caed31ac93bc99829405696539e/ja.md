```
t8_forest_partition_create_tree_offsets(forest)
```

パーティション化されたフォレストの配列ツリーオフセットを作成します。この配列は、位置 p にこのプロセスの最初のツリーのグローバル ID を格納します。もしこのツリーが共有されている場合は、-(global_id) - 1 を格納します。

# 引数

  * `forest`:[in,out] フォレスト。*forest* はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
void t8_forest_partition_create_tree_offsets (t8_forest_t forest);
```
