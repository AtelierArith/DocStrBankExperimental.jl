```
t8_stash_get_attribute_id(stash, index)
```

指定された属性の package_id を返します。

# 引数

  * `stash`:[in] 考慮すべきスタッシュ。
  * `index`:[in] *stash* の属性配列における属性のインデックス。

# 戻り値

属性の package_id。

### プロトタイプ

```c
int t8_stash_get_attribute_id (t8_stash_t stash, size_t index);
```
