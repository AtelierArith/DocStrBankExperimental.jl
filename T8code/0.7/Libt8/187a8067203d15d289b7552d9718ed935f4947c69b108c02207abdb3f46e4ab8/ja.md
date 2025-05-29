```
t8_forest_set_user_data(forest, data)
```

フォレストのユーザーデータを設定します。これは、適応ルーチンにユーザー定義の引数を渡すために使用できます。

# 引数

  * `forest`:[in,out] フォレスト
  * `data`:[in] ユーザーデータへのポインタ。t8codeはデータに触れることはありません。この関数を呼び出す前にフォレストをコミットする必要はありません。

# 参照

[`t8_forest_get_user_data`](@ref)

### プロトタイプ

```c
void t8_forest_set_user_data (t8_forest_t forest, void *data);
```
