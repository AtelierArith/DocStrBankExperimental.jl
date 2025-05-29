```
t8_forest_get_local_num_elements(forest)
```

フォレスト内のプロセスローカル要素の数を返します。

# 引数

  * `forest`:[in] フォレスト。

# 戻り値

このプロセスの*forest*内の要素の数。*forest*はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_locidx_t t8_forest_get_local_num_elements (const t8_forest_t forest);
```
