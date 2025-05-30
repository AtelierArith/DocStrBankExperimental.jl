```
t8_forest_iterate_replace(forest_new, forest_old, replace_fn)
```

2つの森林があり、一方の森林の要素は他方の森林の要素の直接の子または親である場合、2つの森林を比較し、古い森林の各洗練された要素または粗いファミリーに対して、古い要素と新しい要素のローカルインデックスを提供するコールバック関数を呼び出します。

!!! note
    *replace_fn*にユーザーポインタを渡すには、t8*forest*set*user*dataおよびt8*forest*get*user*dataを使用します。


# 引数

  * `forest_new`:[in] 新しい森林、各要素は*forest_old*の要素の親または子です。
  * `forest_old`:[in] 初期の森林。
  * `replace_fn`:[in] 置換コールバック関数。

### プロトタイプ

```c
void t8_forest_iterate_replace (t8_forest_t forest_new, t8_forest_t forest_old, t8_forest_replace_t replace_fn);
```
