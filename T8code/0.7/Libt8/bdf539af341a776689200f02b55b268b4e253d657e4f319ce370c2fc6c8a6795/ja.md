```
t8_stash_get_attribute_tree_id(stash, index)
```

指定された属性が属するツリーのIDを返します。

# 引数

  * `stash`:[in] 考慮すべきスタッシュ。
  * `index`:[in] *stash* の属性配列における属性のインデックス。

# 戻り値

ツリーID。

### プロトタイプ

```c
t8_gloidx_t t8_stash_get_attribute_tree_id (t8_stash_t stash, size_t index);
```
