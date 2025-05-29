```
t8_forest_get_tree_element_offset(forest, ltreeid)
```

ローカルツリーの要素オフセットを返します。これは、すべてのツリーの中で小さいローカルツリーIDを持つツリーの要素数です。

!!! note
    *forest* はこの関数を呼び出す前にコミットされている必要があります。


# 引数

  * `forest`:[in] フォレスト。
  * `ltreeid`:[in] ツリーのローカルID。

# 戻り値

IDが *ltreeid* より小さいすべてのローカルツリーの葉要素の数。

### プロトタイプ

```c
t8_locidx_t t8_forest_get_tree_element_offset (const t8_forest_t forest, const t8_locidx_t ltreeid);
```
