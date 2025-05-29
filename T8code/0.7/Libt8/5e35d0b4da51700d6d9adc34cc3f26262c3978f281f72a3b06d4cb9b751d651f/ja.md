```
t8_forest_new_adapt(forest_from, adapt_fn, recursive, do_face_ghost, user_data)
```

別の森林から適応された森林を構築します。

!!! note
    これは、t8*forest*init、t8*forest*set*adapt、t8*forest*set*ghost、およびt8*forest*commitを呼び出すことと同等です。


# 引数

  * `forest_from`:[in] 精練する森林
  * `adapt_fn`:[in] 使用する適応関数
  * `replace_fn`:[in] 使用する置換関数
  * `recursive`:[in] trueの場合、適応は再帰的です
  * `do_face_ghost`:[in] trueの場合、森林のためにゴースト要素の層が作成されます。
  * `user_data`:[in] NULLでない場合、森林のユーザーデータポインタがこの値に設定されます。

# 戻り値

*forest_from*から適応された新しい森林。

### プロトタイプ

```c
t8_forest_t t8_forest_new_adapt (t8_forest_t forest_from, t8_forest_adapt_t adapt_fn, int recursive, int do_face_ghost, void *user_data);
```
