```
t8_forest_get_user_data(forest)
```

フォレストに関連付けられたユーザーデータポインタを返します。

# 引数

  * `forest`:[in] フォレスト。

# 戻り値

*forest* のユーザーデータポインタ。フォレストは、この関数を呼び出す前にコミットされている必要はありません。

# 参照

[`t8_forest_set_user_data`](@ref)

### プロトタイプ

```c
void * t8_forest_get_user_data (const t8_forest_t forest);
```
