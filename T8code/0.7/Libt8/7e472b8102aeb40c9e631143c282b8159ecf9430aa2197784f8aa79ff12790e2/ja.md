```
t8_forest_get_global_num_elements(forest)
```

フォレスト内のグローバル要素の数を返します。

# 引数

  * `forest`:[in] フォレスト。

# 戻り値

*forest*内の要素の数（すべてのプロセスで合計）。この関数を呼び出す前に*forest*はコミットされている必要があります。

### プロトタイプ

```c
t8_gloidx_t t8_forest_get_global_num_elements (const t8_forest_t forest);
```
