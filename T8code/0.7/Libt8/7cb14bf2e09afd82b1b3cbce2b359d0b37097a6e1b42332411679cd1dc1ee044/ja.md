```
t8_forest_get_element_in_tree(forest, ltreeid, leid_in_tree)
```

フォレスト内のローカルツリーの要素を返します。

!!! note
    ツリーIDがわかっている場合、この関数はt8*forest*get_elementよりも優先されるべきです。*forest*はこの関数を呼び出す前にコミットされている必要があります。


# 引数

  * `forest`:[in] フォレスト。
  * `ltreeid`:[in] フォレスト内のローカルツリーのID。
  * `leid_in_tree`:[in] ツリー内の要素のインデックス。

# 戻り値

要素へのポインタ。

### プロトタイプ

```c
const t8_element_t * t8_forest_get_element_in_tree (t8_forest_t forest, t8_locidx_t ltreeid, t8_locidx_t leid_in_tree);
```
