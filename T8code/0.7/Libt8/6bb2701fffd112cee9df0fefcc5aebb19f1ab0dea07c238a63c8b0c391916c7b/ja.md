```
t8_forest_element_is_leaf(forest, element, local_tree)
```

与えられた要素がフォレストの葉であるかどうかを照会します。

!!! note
    これはゴーストリーフを照会しません。


!!! note
    *forest* はこの関数を呼び出す前にコミットされている必要があります。


# 引数

  * `forest`:[in] フォレスト。
  * `element`:[in] *forest* のローカルツリーの要素。
  * `local_tree`:[in] *forest* のローカルツリーID。

# 戻り値

*element* が *forest* の *local_tree* の葉である場合にのみ、真（非ゼロ）を返します。

### プロトタイプ

```c
int t8_forest_element_is_leaf (const t8_forest_t forest, const t8_element_t *element, const t8_locidx_t local_tree);
```
