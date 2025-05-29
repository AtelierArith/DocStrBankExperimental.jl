```
t8_forest_get_user_function(forest)
```

フォレストに関連付けられたユーザ関数ポインタを返します。

# 引数

  * `forest`:[in] フォレスト。

# 戻り値

*forest* のユーザ関数ポインタ。 この関数を呼び出す前にフォレストをコミットする必要はありません。

# 参照

[`t8_forest_set_user_function`](@ref)

### プロトタイプ

```c
t8_generic_function_pointer t8_forest_get_user_function (const t8_forest_t forest);
```
