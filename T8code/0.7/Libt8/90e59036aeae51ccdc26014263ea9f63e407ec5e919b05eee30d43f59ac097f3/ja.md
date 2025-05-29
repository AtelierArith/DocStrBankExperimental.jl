```
t8_forest_get_element(forest, lelement_id, ltreeid)
```

フォレストの要素を返します。

!!! note
    この関数は二分探索を行います。定数アクセスのためには、t8*forest*get*element*in_treeを使用してください。*forest*はこの関数を呼び出す前にコミットされている必要があります。


# 引数

  * `forest`:[in] フォレスト。
  * `lelement_id`:[in] *forest*内の要素のローカルID。
  * `ltreeid`:[out] NULLでない場合、出力時に要素が存在する木のローカルツリーID。

# 戻り値

要素へのポインタ。要素が存在しない場合はNULL。

### プロトタイプ

```c
t8_element_t * t8_forest_get_element (t8_forest_t forest, t8_locidx_t lelement_id, t8_locidx_t *ltreeid);
```
