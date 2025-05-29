```
t8_forest_partition_create_offsets(forest)
```

パーティション化されたフォレストの element_offset 配列を作成します。

# 引数

  * `forest`:[in,out] フォレスト。*forest* はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
void t8_forest_partition_create_offsets (t8_forest_t forest);
```
