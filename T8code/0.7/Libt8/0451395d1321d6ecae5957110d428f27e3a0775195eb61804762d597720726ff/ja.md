```
t8_forest_set_user_function(forest, _function)
```

フォレストのユーザ関数ポインタを設定します。これは、適応ルーチンにユーザ定義関数を渡すために使用できます。

!!! note
    *function* は、あなたの選択による戻り値とパラメータを持つ任意の関数であることができます。t8*forest*get*user*functionでアクセスする際には、適切な型にキャストする必要があります。


# 引数

  * `forest`:[in,out] フォレスト
  * `function`:[in] ユーザ定義関数へのポインタ。t8codeはこの関数に触れることはありません。この関数を呼び出す前にフォレストをコミットする必要はありません。

# 参照

[`t8_forest_get_user_function`](@ref)

### プロトタイプ

```c
void t8_forest_set_user_function (t8_forest_t forest, t8_generic_function_pointer function);
```
