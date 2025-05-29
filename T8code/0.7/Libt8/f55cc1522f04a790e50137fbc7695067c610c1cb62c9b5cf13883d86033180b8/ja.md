```
t8_forest_get_num_ghosts(forest)
```

フォレストのゴースト要素の数を返します。

# 引数

  * `forest`:[in] フォレスト。

# 戻り値

*forest* のゴースト構造に格納されているゴースト要素の数。ゴーストが構築されていない場合は 0。

# 参照

[`t8_forest_set_ghost`](@ref) *forest* はこの関数を呼び出す前にコミットされている必要があります。

### プロトタイプ

```c
t8_locidx_t t8_forest_get_num_ghosts (const t8_forest_t forest);
```
